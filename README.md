# Bujku Dataset

## Overview

The Bujku dataset is a collection of text and dense vector embeddings derived from segmented articles of the daily newspaper 'Bujku.' This newspaper served as a crucial source of independent information for Kosovo Albanians during the 1990s, a time of significant social and political upheaval under Serbian oppression. The dataset spans from 1991 to 1998 and is intended to facilitate research in areas such as history, linguistics, and digital humanities.

The dataset was created by segmenting articles from scanned issues of 'Bujku' and applying optical character recognition (OCR) using Gemini Flash 1.5 and Tesseract. Dense vector representations of the articles were then generated using a multilingual text embedding model.

## Context and Motivation

Following the suppression of Kosovo's autonomy by Serbian authorities in 1989, media outlets in the Albanian language were heavily censored, and nearly all independent news sources were shut down. In response, 'Bujku' evolved from a focus on agricultural issues to becoming a critical voice of peaceful resistance and a source of reliable news for Kosovo Albanians.

FLOSSK, a local NGO, undertook efforts to scan issues of 'Bujku' from 1991 to 1998, providing public access to these historical documents. However, the articles were not individually segmented, making detailed analysis difficult. This dataset aims to provide researchers and historians with article-level access to 'Bujku' content for better analysis and archiving.

## Loading the Dataset

Before using the dataset, please note that you need to request and obtain access from the dataset owner on HuggingFace.

Once access is granted, you can use the following code to load the dataset using the `datasets` library from HuggingFace:

```python
# pip3 install datasets
from datasets import load_dataset

dataset = load_dataset("Kushtrim/bujku")

# View a sample of the dataset
print(dataset['train'][0])
```

## Dataset Details

### Data Collection

- **Source**: The issues were obtained from [FLOSSK's digital archive](https://books.flossk.org/gazetat/).
- **Issues Downloaded**: 1834 issues were manually downloaded and organized by publication date.
- **Format**: Original filenames, such as `BU-YYYYMMDD.pdf`, were preserved to maintain the context and facilitate retrieval.

### Segmentation Methodology

The segmentation of articles was a complex task due to the newspaper's layout. Articles often spanned multiple columns with overlapping content. Manual segmentation was carried out based on visual cues such as headlines and formatting, ensuring accurate delineation of articles. A total of 130,046 articles were successfully segmented.

### OCR Processing

Two OCR tools were used:
- **Gemini Flash 1.5**: Provided superior accuracy, particularly in handling multi-column layouts and recognizing Albanian special characters (e.g., ç, ë) and older typographical symbols (« and »).
- **Tesseract**: Served as a fallback for around 5% of the articles, mainly those with complex layouts or faint text.

The combination of these tools resulted in a high-quality transcription of the articles.

### Embedding Extraction

To enable semantic search and analysis, dense vector representations of the articles were extracted using the `intfloat/multilingual-e5-large` model, which generates embeddings suited for multilingual text, including Albanian. This allows for various tasks such as thematic clustering, content similarity searches, and discourse analysis.

### Platform for Exploration

The dataset is accompanied by a web platform, [Bujku Platform](https://bujku.news), which provides:
- **Semantic Search**: Leveraging embeddings to allow users to search articles by their semantic content.
- **Easy Browsing**: Users can explore and read the digitized articles of 'Bujku.'

## Technical Report

For a detailed overview of the dataset creation process, challenges, and methodology, please refer to the [Technical Report](https://github.com/KushtrimVisoka/bujku/blob/6a6243e29cb63b7431c9c2e172756639dd9b3392/Bujku.pdf).


## Applications

The Bujku dataset is a valuable resource for:
- **Historical Research**: Gaining insights into Kosovo's sociopolitical context during the 1990s.
- **Linguistic Studies**: Analyzing the evolution of the Albanian language in media.
- **Digital Humanities**: Exploring trends and narratives within the newspaper content.

## Limitations and Future Work

While the dataset provides a comprehensive view of 'Bujku,' certain limitations exist:
- **Incomplete Issues**: Some issues are missing, leaving gaps in the archive.
- **Manual Segmentation**: A labor-intensive process that could benefit from more automation.

Future enhancements may include adding metadata for each article, improving segmentation accuracy with advanced models, and incorporating any newly discovered issues.

## Citation

@misc{visoka2024digitalarchive,
    author = {Kushtrim Visoka},
    title = {Creating a Digital Archive: Segmenting and Transcribing Articles from the Daily Newspaper ‘Bujku’},
    year = {2024},
    howpublished = {\url{https://github.com/KushtrimVisoka/bujku}},
}
