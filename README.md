# Assignment: Create a stopwatch service

Have fun!

## Part 1

  1. Create a REST service running on Azure, using Owin and Web API, that implements the API specification below.
      - Timer states should be stored in Azure Table Storage.
      - Limit access to the system by requiring user authentication.
      - A user is only allowed to see and modify their own stopwatches.

### API Specification

#### POST /api/stopwatch

Create / reset a stopwatch.

Request body:

    {
       "name": [string, stopwatch name]
    }
    

#### GET /api/stopwatch

Returns the elapsed time for each stopwatch created by the logged on user, in milliseconds.

Response body: 

    {
        [string, stopwatch name]: [int, elapsed milliseconds],
        [string, stopwatch name]: [int, elapsed milliseconds],
        [string, stopwatch name]: [int, elapsed milliseconds],
        [string, stopwatch name]: [int, elapsed milliseconds],
        ...
    }

## Part 2

  2. Create the endpoint specified below.

      - A user is only allowed to see the stopwatches with a certain name if they "own" a
        stopwatch with the same name.
      - If a user does not own a stopwatch with given name, the endpoint should return an
        appropriate error response.

### API Specification

#### GET /api/stopwatch/[stopwatch name]

Returns the elapsed time for all the stopwatches with given stopwatch name.

Response body: 

    {
        [string, user name]: [int, elapsed milliseconds],
        [string, user name]: [int, elapsed milliseconds],
        [string, user name]: [int, elapsed milliseconds],
        [string, user name]: [int, elapsed milliseconds],
        ...
    }

## Part 3

  3. How would the performance of the endpoints described above change if the number of active users grew to tens/hundreds of thousands given that every user creates/requests stopwatches once per minute...
      a. ... for the endpoints in [Part 1](#part-1)?
      b. ... for the endpoint in [Part 2](#part-2)?
  4. How to mitigate performance degradation and make the system capable of handling such a load...
      a. ... with a redesign of the table structure in Azure Table Storage?
      b. ... with other technologies available on the Azure platform?
      c. ... with technologies from other cloud platforms?

## Part 4 

We want a web client to show real time values for the stopwatches. This means that whenever the owner of a stopwatch resets it, that stopwatch should restart in the client window.

  5. Design an architecture that is suitable for this in a large scale.    
     Explain what technologies you would use, and what the pros and cons are of each of these.    
     Where applicable, indicate what alternatives there are for the choices you made.

