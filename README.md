###Step 1: Obtain an access token 

Request:

```
 curl -X POST -H "Content-Type: application/json" \
      --user "<client_id>:<client_secret>" \
      -d '{"grant_type": "client_credentials", "scope": "public"}' \
      'https://api.lyft.com/oauth/token' 
```
   
Response: 

```
{"token_type": "Bearer", \
"access_token": "gAAAAABYm6lgCnbmN1CdSBY4_vHTK6UKmTAR4SCFM0-J520w10Nr1Ikv8yy8-fgvxIDGc3oHMiqFvRCCckdY9LFSGuuAE3AZCWDkra
```

###Step 2: Cost
A GET to the /cost endpoint that returns the estimated cost, distance, duration and most importantly the primetime_percentage.

Request:

```
curl --include -X GET -H 'Authorization: bearer <bearer_token>' \
     'https://api.lyft.com/v1/cost?start_lat=37.7772&start_lng=-122.4233&end_lat=37.7972&end_lng=-122.4533'
```

Response:

```json
{"cost_estimates": [{"ride_type": "lyft_plus", "estimated_duration_seconds": 833, "estimated_distance_miles": 3.18, "estimated_cost_cents_max": 1975, "primetime_percentage": "0%", "is_valid_estimate": true, "currency": "USD", "estimated_cost_cents_min": 1175, "display_name": "Lyft Plus", "primetime_confirmation_token": null, "can_request_ride": true}, {"ride_type": "lyft_line", "estimated_duration_seconds": 838, "estimated_distance_miles": 3.11, "estimated_cost_cents_max": 437, "primetime_percentage": "0%", "is_valid_estimate": true, "currency": "USD", "estimated_cost_cents_min": 437, "display_name": "Lyft Line", "primetime_confirmation_token": null, "can_request_ride": true}, {"ride_type": "lyft", "estimated_duration_seconds": 833, "estimated_distance_miles": 3.18, "estimated_cost_cents_max": 1375, "primetime_percentage": "0%", "is_valid_estimate": true, "currency": "USD", "estimated_cost_cents_min": 775, "display_name": "Lyft", "primetime_confirmation_token": null, "can_request_ride": true}]}
```