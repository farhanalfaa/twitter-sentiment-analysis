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
array_of_users= ['pieterpitojo','rullyjoo277212','dee13431735','noveriani5','johnbralink',
                 'lamegogosa','yusrinacindil','boimakar','bgs_aulia', 'kembangmlathi', 'tristyanto76', 
                 'hayanaqu', 'cahyaadiputra7', 'roon3651', 'indahmel2', 'adoeldian', 'bagus_ardiansyh', 
                 'failcodes', 'azhry', 'hasbiziyadi', 'danarjon', 'andibayy', 'mhrsnty', 'erwepp', 'neng_jeprett', 
                 'zahrafaiza', 'angggiita', 'rmarlendi', 'fjarr_', 'iqbalmt06', 'ibnoemoesa', 'mathiinulhakim', 
                 'encenggondok15', 'ben_panji', 'aghuzk', 'rosydin17', 'sandi_alfarizie', 'rerew__', 'gianhervyagi', 
                 'imancibiuk99', 'adiosbxxch', 'jaluhpp', 'sahastiwi_endah', 'dancinseaweed', 'ardy1905', 'ricckyrpl', 
                 'farahsumayya', 'syahidun58', 'kenyulian', 'manakutau_mas', 'misbahulmunawa6', 'zoelfian18_', 'ceemplon', 
                 'talass_19', 'sh3_think', 'benuuir', 'lenyastriani', 'iboylagi', 'desartha', 'helminoris22', 'sitimaysarohxix', 
                 'rizqosyahril', 'djaya_karta', '_heyliaaa', 'boiisoasoapapu','smuhamad049', 'kamilmjd', 'hasbiarraihanm','ranasclok', 
                 'rizky_achmad_','yuskapityaji','ortsasybur', 'kammenrider', 'uniqnyaunii', 'ahmad_richad','antonwahyudi20','albabalpachino',
                 'fr_rudin', 'hendrajlek', 'madimaks17', 'ibnu_dumadi', 'rullypratama84','mbritodysey', 'darwiz_one', 'g_apunk', 'alvinmp', 
                 'miamariau', 'le_roslina', 'wayan_ekmt', 'akhmal_em', 'yoganugr', 'nyonriers', 'maukesana', 'adelle_ap', 'ilyas_arin','widadms17', 
                 'hasabibilal','cerita_lakon50' ,'razief991', 'rizkymaryadi','neaaara3', 'amrin_marvf','rahmatp_id', 'ikhwanusshofaM', 
                 'haremarem', 'bogiyuniar','riafiani', 'taufiqmarhab','helelsson', 'andhikopaw','serasamerdek', 'mutiaaksmi',
                 'ohsigalih', 'silviasanad','nurynprabw','beelloman', 'alanzhoo', 'komiichan96','farhanalfaaa', 'akupundemiki', 
                 'faisalmahrus50', 'ranicyn',  'nonyuliii',  'boyhendryko', 'ifanugrh', 'yuliantonuh', 'djoko_saja', 'putra_matra', 
                 'azmii_aziz', 'rendy_ris', 'nursii5', 'edoriydho', 'teguh98cc', 'anindramoelya', 'robbyanto90', 'rahmadiheru88', 
                 'rezimtipudaya', 'gunturmataram', 'srisumaryani', 'beny_fian', 'aryoramangan', 'dinarsbakti', 'ivansiregar18', 
                 'nnadzifah', 'apaajadehyaok', 'marsha_chichi', 'adamnain', 'audicipt', 'farisalfarabi11', 'maslan_zr', 'nrrmlhs', 
                 'yogarendras', 'rubkaryo323', 'fanimaya', 'adilmer4', 'ikawahyu_n', 'bolehdikosongin', 'welgeduwel_beh', 'kikihakim', 
                 'paol_paul', 'namanyasisca', 'ariefsulaiman02', 'qaddim_95', 'refkafm', 'nurwahyudin460', 'iqramuh_', 'xmerissax', 
                 'ahmad310017', 'dnswr__', 'godx1va', 'devinnugroho1', 'vbottaega', 'sfambrr', 'hdafi', 'reykurihiku', 'apasihrii', 
                 'usaisudahhh', 'sarwohadi_p', 'ekakaay', 'ezash', 'yumglg', 'danangsett', 'ayy_only', 'intplp']
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
