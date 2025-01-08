# Sturdy Stats SDK

This is the sdk for the [Sturdy Statistics API](https://sturdystatistics.com/). 

## Technical Features

<dl><dt>Automatic Structuring of Unstructured Text Data</dt><span></span><dd>Convert unstructured documents into structured formats, allowing seamless analysis alongside traditional tabular data.<a href="https://sturdystatistics.com/features.html#structure"> Learn More &gt;</a></dd><span></span><dt>Explainable Text Classification</dt><span></span><dd>Gain clear insights into how text data is categorized, while enhancing transparency and trust in your analyses.<a href="https://sturdystatistics.com/features.html#classification"> Learn More &gt;</a></dd><span></span><dt>Effective with Small Datasets</dt><span></span><dd>Achieve meaningful results even with limited data, making our solutions accessible to organizations of all sizes.<a href="https://sturdystatistics.com/features.html#sparse-prior"> Learn More &gt;</a></dd><span></span><dt>Powerful Search Capabilities</dt><span></span><dd>Leverage our robust search API to retrieve and analyze specific information within your unstructured data.<a href="https://sturdystatistics.com/features.html#search"> Learn More &gt;</a></dd><span></span><dt>Comprehensive Data Lake</dt><span></span><dd>Store and analyze all your data — structured and unstructured — in one place, facilitating holistic insights.<a href="https://sturdystatistics.com/features.html#data-lake"> Learn More &gt;</a></dd><span></span></dl>

## Quickstart

Create a Index from scratch
```python
from sturdystats import Index, Job
import pandas as pd

API_KEY = "XXX"
df = pd.read_parquet('data/optimization_abstracts.parquet')

index = Index(API_key=API_KEY, name='quickstart_cs.LG_version1')
res = index.upload(df.to_dict("records"))
job = index.train(params=dict(), fast=True, wait=True)
```

Explore Your Data
```python
import plotly.express as px
df_topic = pd.DataFrame(index.topicSearch()['topics'])

import plotly.express as px
fig = px.sunburst(
    df_topic, 
    path=["topic_group_short_title", "short_title"],
    values="prevalence", 
    hover_data=["topic_id"]
)
```

{% include_relative sunburst.html %} 



