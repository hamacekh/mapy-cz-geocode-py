# mapy-cz-geocode
Get coordinates and location for given geographic entity (e.g. address, city, WGS coordinates)

This Python package is automatically generated by the [OpenAPI Generator](https://openapi-generator.tech) project:

- API version: 1.0.0
- Package version: 1.0.0
- Build package: org.openapitools.codegen.languages.PythonClientCodegen

## Requirements.

Python 3.7+

## Installation & Usage
### pip install

If the python package is hosted on a repository, you can install directly using:

```sh
pip install git+https://gitlab.com/hamacekh/mapy-cz-geocode-py.git
```
(you may need to run `pip` with root permission: `sudo pip install git+https://gitlab.com/hamacekh/mapy-cz-geocode-py.git`)

Then import the package:
```python
import mapy_cz_geocode
```

### Setuptools

Install via [Setuptools](http://pypi.python.org/pypi/setuptools).

```sh
python setup.py install --user
```
(or `sudo python setup.py install` to install the package for all users)

Then import the package:
```python
import mapy_cz_geocode
```

### Tests

Execute `pytest` to run the tests.

## Getting Started

Please follow the [installation procedure](#installation--usage) and then run the following:

```python

import time
import mapy_cz_geocode
from mapy_cz_geocode.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://api.mapy.cz
# See configuration.py for a list of all supported configuration parameters.
configuration = mapy_cz_geocode.Configuration(
    host = "https://api.mapy.cz"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: headerApiKey
configuration.api_key['headerApiKey'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['headerApiKey'] = 'Bearer'

# Configure API key authorization: queryApiKey
configuration.api_key['queryApiKey'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['queryApiKey'] = 'Bearer'


# Enter a context with an instance of the API client
with mapy_cz_geocode.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = mapy_cz_geocode.GeocodingApi(api_client)
    query = '' # str | Geographic entity name to resolve (optional) (default to '')
    lang = mapy_cz_geocode.Language() # Language | Preferred language for result entity names (optional)
    limit = 5 # int | Maximum number of results (default 5, upper limit 15) (optional) (default to 5)
    type = ["regional","poi"] # List[GeocodeEntityType] | Return selected entity types only (optional) (default to ["regional","poi"])
    locality = ['locality_example'] # List[str] | Return results only from these localities. It may be in form of comma-separated locality names (e. g. `Praha 5`, `Lhota u Kolína`), country codes (cz, gb, us, ...) or rectangles `BOX({minLon},{minLat},{maxLon},{maxLat})` or a mix of them. Location names (except country codes) are internally converted to bounding boxes, so using box arguments is preferred to avoid ambiguities - resolved boxes for locality names are returned in response (or \"Not found!\" for unknown localities) to help with this. On the other hand, country codes are preferred over their bounding boxes, because they allow precise filtering and avoid enge-cases near the date-line.  (optional)
    prefer_b_box = [3.4] # List[float] | Prefer results from this box (not a filter). Conflicts with `near`. If neither `box` nor `near` is specified, defaults to Czech Republic. Format `{minLon},{minLat},{maxLon},{maxLat}` (optional)
    prefer_near = [3.4] # List[float] | Prefer results near this position (not a filter). Conflicts with `box`. If neither `box` nor `near` is specified, defaults to Czech Republic. Format `{lon}, {lat}` (optional)
    prefer_near_precision = 3.4 # float | Precision of parameter `near` in meters (use to prefer results from a circle) (optional)

    try:
        # Find entities for given search query
        api_response = api_instance.api_geocode_v1_geocode_get(query=query, lang=lang, limit=limit, type=type, locality=locality, prefer_b_box=prefer_b_box, prefer_near=prefer_near, prefer_near_precision=prefer_near_precision)
        print("The response of GeocodingApi->api_geocode_v1_geocode_get:\n")
        pprint(api_response)
    except ApiException as e:
        print("Exception when calling GeocodingApi->api_geocode_v1_geocode_get: %s\n" % e)

```

## Documentation for API Endpoints

All URIs are relative to *https://api.mapy.cz*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*GeocodingApi* | [**api_geocode_v1_geocode_get**](docs/GeocodingApi.md#api_geocode_v1_geocode_get) | **GET** /v1/geocode | Find entities for given search query
*GeocodingApi* | [**api_rgeocode_v1_rgeocode_get**](docs/GeocodingApi.md#api_rgeocode_v1_rgeocode_get) | **GET** /v1/rgeocode | Get regional entities for coordinates
*GeocodingApi* | [**api_suggest_v1_suggest_get**](docs/GeocodingApi.md#api_suggest_v1_suggest_get) | **GET** /v1/suggest | Suggest entities while typing a query


## Documentation For Models

 - [Coordinates](docs/Coordinates.md)
 - [GeocodeEntityType](docs/GeocodeEntityType.md)
 - [GeocodeResult](docs/GeocodeResult.md)
 - [GeocodeResultEntity](docs/GeocodeResultEntity.md)
 - [HTTPValidationError](docs/HTTPValidationError.md)
 - [Language](docs/Language.md)
 - [RegionalEntity](docs/RegionalEntity.md)
 - [RgeoEntityType](docs/RgeoEntityType.md)
 - [RgeocodeResult](docs/RgeocodeResult.md)
 - [RgeocodeResultEntity](docs/RgeocodeResultEntity.md)
 - [ValidationError](docs/ValidationError.md)
 - [ValidationErrorLocInner](docs/ValidationErrorLocInner.md)


<a id="documentation-for-authorization"></a>
## Documentation For Authorization


Authentication schemes defined for the API:
<a id="headerApiKey"></a>
### headerApiKey

- **Type**: API key
- **API key parameter name**: X-Mapy-Api-Key
- **Location**: HTTP header

<a id="queryApiKey"></a>
### queryApiKey

- **Type**: API key
- **API key parameter name**: apikey
- **Location**: URL query string


## Author




