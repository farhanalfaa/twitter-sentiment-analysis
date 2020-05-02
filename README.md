# Twitter-Sentiment Analysis

Sentiment Classification using Fasttext Embeddings with Convolutional Neural Networks (CNN)

## Getting Started

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur malesuada orci ante, a dictum libero bibendum vitae. Curabitur vehicula interdum feugiat. Sed feugiat tincidunt fermentum.

[![Generic badge](https://img.shields.io/badge/fastText-0.9.2-BLUE.svg)](https://github.com/facebookresearch/fastText/)

### Prerequisites

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

### Build With

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

### Installing

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

## Features

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

### [Part 1] Crawling Twitter Data

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

#### Install Library

```python
pip install twitterscraper
```

#### Import Library

```python
import pandas as pd
import twitterscraper as ts
```

#### Setup User Data

```python
array_of_users= ['user1', 'user2', ..., 'userN']
```

#### Crawling Process

```python
import time
start_time = time.time()

limit = 50

list_tweets = []
tweets      = [None] * len(array_of_users)

for i in range(0, len(array_of_users)):
  tweets[i]   = ts.query.query_tweets_from_user(array_of_users[i], limit=limit)
  list_tweets.append(tweets[i])

print("--- %s seconds ---" % (time.time() - start_time))
```

#### Convert into Single List

```python
import itertools
merged = list(itertools.chain(*list_tweets))
```

#### Convert into DataFrame

```python
df = pd.DataFrame(t.__dict__ for t in merged)
```

#### Export to CSV File

```python
from google.colab import files

result.to_csv('dataset_result.csv', index=False, sep='~') 
files.download('dataset.csv')
```



### [Part 2] Exploratory Data Analysis

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

### [Part 3] Fasttext Embeddings

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

### [Part 4] Convolutional Neural Network

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

## Deployment

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

## Contributing

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

## Versioning

Donec velit urna, commodo vel tempus vitae, tristique ut erat. Pellentesque aliquam tristique justo, id tempor turpis vehicula sed. Phasellus a pretium mauris. Pellentesque nec pretium magna.

## Authors
  [Farhan Alfariqi](https://github.com/farhanalfaa)
