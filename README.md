# AmazonScraper

Retrieve data on the closest item on Amazon corresponding to a given search term or directly using an ASIN.

## Installation

1. Get [Python Poetry](https://python-poetry.org/)
2. `cd` into the root of this repository
3. Run `poetry install`

## Usage

### Fetch Reviews by Search Query
Retrieve reviews for the closest product on Amazon based on a search query.
```python
from src.amazon import AmazonScraper

search_query = 'ipad air'
scraper = AmazonScraper()

reviews = scraper.get_closest_product_reviews(search_query, num_reviews=25)

print(reviews)
# [{'customer_name': 'Kenova Pelletier', 'rating': 1, 'review': 'This looked amazing out of the box...
```

### Fetch Reviews by ASIN
Retrieve reviews for a specific product on Amazon using its ASIN.
```python
from src.amazon import AmazonScraper

product_asin = 'B08J65DST5'
scraper = AmazonScraper()

reviews = scraper.get_product_reviews_by_asin(product_asin, num_reviews=25)

print(reviews)
# [{'customer_name': 'carol anderson', 'rating': 1, 'review': 'This was my first Apple product...
```

#### Debug Flag
The `get_closest_product_reviews` and `get_product_reviews_by_asin` methods also have a `debug` flag available that outputs the total time taken for execution.

```python
search_query = 'ipad air'
scraper = AmazonScraper()

reviews = scraper.get_closest_product_reviews(search_query, num_reviews=5, debug=True)
# 13.47 seconds taken
```

```python
product_asin = 'B08J65DST5'
scraper = AmazonScraper()

reviews = scraper.get_product_reviews_by_asin(product_asin, num_reviews=5, debug=True)
# 10.12 seconds taken
```

## Command Line Usage
You can also use this tool from the command line to fetch reviews by either search query or ASIN.

#### Fetch Reviews by Search Query (CLI)
```sh
python src/amazon.py --query "ipad air" 5 --headless --debug
```

#### Fetch Reviews by ASIN (CLI)
```sh
python src/amazon.py --asin "B08J65DST5" 5 --headless --debug
```

Note that the `--headless` and the `--debug` flags are optional.

## Disclaimer
This project is intended for personal and educational purposes only. Any use of this project for commercial or production purposes is not recommended. The author does not take responsibility for any misuse or consequences arising from the use of this project outside of its intended scope.
