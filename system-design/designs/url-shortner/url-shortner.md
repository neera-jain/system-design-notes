# URL Shortner
Here we design a URL Shortner System

## Requirements
### Functional Requirements
- Given a long URL return a short URL
- When user hits a short URL, redirect to long URL

### Non-functional Requirements
- Highly available
- Low Latency

### Scale
This is a read and write heavy application.
- Write operation
    * 100 million URLs to be generated per day
    * 100 million / (24 * 60 * 60) = 1160 per second
- Read operation
    * Assuming a ratio of read to write is 10:1
    11600 operations per second
- Storage
    * Assuming this application runs for 10 years. Number of  URLs generated :
    100 million * 365 * 10 = 365 billion records
    * To handle this quantity of records, Cassandra can be used for database.

### High Level Design
- System Design Diagram

- API required
    * URL shortening <br>
        To create a new short URL, a client sends a POST request which contains only 1 paramete : original long URL <br>
        POST - api/v1/data/shorten <br>
        Request Param : {longURL : ''} <br>
        Returns a short URL

    * URL Redirecting <br>
      To redirect a short URL to the corresponding long URL, client sends a GET request <br>
      GET - api/v1/data/shortURL
      Returns a long URL for redirection

### Design Deep Dive
- Redirection 
    * HTTP 301 redirect. It shows that the requested URL is "permanently" moved to the long URL. Since it is permanently moved, the browser caches the response and subsequent requests for the same URL will not be sent to the short URL service. Instead requests are redirected to the long URL directly.

    * HTTP 302 redirect. It means that the URL is temporarily moved to the long URL, meaning that the subsequent requests for the same URL will be sent to the short URL service first, and then will be redirected to the returned long URL.

    * Each redirection method has its pros and cons. If the priority is to reduce the server load, using 301 is preferred. However, if the analytics are important, 302 is a better choice as it can track click rate and source of the click more easily.

- URL Encoding <br>
Our system's primary goal is to shorten a given URL, let's look at different approaches:
    * Base62 Approach <br>
    In this approach, we can encode the original URL using Base62 which consists of the capital letters A-Z, the lower case letters a-z, and the numbers 0-9.
    Where,N: Number of characters in the generated URL. <br>
    So, if we want to generate a URL that is 7 characters long, we will generate ~3.5 trillion different URLs.

    
