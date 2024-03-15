---
title: 
tags:
  - python
  - API
---
- API
    - what is API
        - communication layer between systems without understanding exactly what each other does
        - calling a API = request from a user + response from the server
    - terminology
        - **Base/API URL:** the url allows you to fetch data from
        - **endpoint:**  is a part of the URL that specifies what **resource** you want to fetch. Well-documented APIs usually contain an **API reference**, which is extremely useful for knowing the exact endpoints and resources an API has and how to use them.
        - **consume an API:** use any part of it from your application
    - type of API
        1. **SOAP (Simple Object Access Protocol)** is typically associated with the enterprise world, has a stricter contract-based usage, and is mostly designed around actions. High security
        2. **REST (Representational State Transfer)**
            - is typically used for public APIs and is ideal for fetching data from the web. It’s much lighter and closer to the HTTP specification than SOAP. majority of public APIs are still REST APIs
            - uniform way of interacting with a given server regardless of device or application type using HTTP requests method (get, post, pull, delete)
        3. GraphQL is on the rise and is being adopted by bigger and bigger companies
    - how to call in python
        - install requests package in cmd `$ python -m pip install requests`

        ```python
        import requests
        import json
        import pandas as pd

        #base url + endpoint, use dicts when header and params are needed
        response = requests.get("https://api.thedogapi.com/v1/breeds").json() #.json() print a human-friendly Json format

        data=json.loads(response.text)   #convert Json string into a Python Dictionary; aka "deserialization"
        pd.json_normalize(data) #flatten the nested df + convert into pd_df, neeeded Unserialized data
        ```

    - Authentication
        - **API key:**
            - most common level of authentication, the key is open to public or given to you via specific method (eg email to you after registration on the website)

                ```python
                #example of API key, put the key in the dictionary and pass it into the params argument

                endpoint = "https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos"
                # Replace DEMO_KEY below with your own key if you generated one.
                api_key = "DEMO_KEY"
                query_params = {"api_key": api_key, "earth_date": "2020-07-01"}
                response = requests.get(endpoint, params=query_params)
                response
                ```

        - OAuth:
            - another very common standard but more secure.
            - The server ask the user info. from the 3rd-party and if user pass the credentail identification (eg log-in) the server will send the response for the user request

            ```python
            # Authenticating with OAuth2 in Requests
            from requests_oauthlib import OAuth2Session

            # Inlcude your data
            client_id = "include your client_id here"
            client_secret = "include your client_secret here"
            redirect_uri = "include your redirect URI here"

            # Create a session object
            oauth = OAuth2Session(client_id, redirect_uri = redirect_uri)

            # Fetch a token
            token = oauth.fetch_token("<url to fetch access token>", client_secret = client_secret)

            # Get your authenticated response
            response = oauth.get("URL to the resource")
            ```