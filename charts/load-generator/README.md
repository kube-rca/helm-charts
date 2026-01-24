# Load Generator (k6)

Helm chart to run k6 load against Bookinfo services.

## Values

- `target.baseUrl`: productpage service base URL
- `target.detailsBaseUrl`: details service base URL
- `target.ratingsBaseUrl`: ratings service base URL
- `target.weights.productpage`: productpage traffic weight
- `target.weights.details`: details traffic weight
- `target.weights.ratings`: ratings traffic weight
- `target.rps`: requests per second (RPS)
- `target.duration`: k6 duration
- `target.preAllocatedVUs`: k6 pre-allocated VUs
- `target.maxVUs`: k6 max VUs
- `image.repository`, `image.tag`, `image.pullPolicy`: k6 image settings
