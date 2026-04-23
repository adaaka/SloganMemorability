# Predicting the Memorability of Brand Slogans
Ada Aka and John McCoy

Journal of Marketing (2026)

## Overview

This notebook provides tools to predict **cued brand recall** and **slogan recognition** probabilities for brand slogans using trained models.

This readme deals with the predictions made using slogan_model_predictions.ipynb. This repository also contains a dataset of features for real slogans (in /dataset) which has its own readme.

## Requirements

See requirements.txt

An OpenAI API key is required to generate text embeddings for slogans and brands. The notebook file explains how to obtain such a key.

## Model Predictions

The notebook includes two complementary approaches for predicting slogan memorability:

### 1. Embedding-Based Models

These models predict slogan memorability directly from text embeddings (text-embedding-ada-002).

### 2. Proxy Factors Models

These models use interpretable memorability factors, estimated via embeddings, to make predictions.

## Model files

Pre-trained models to make memorability predictions are stored as .pkl files in /models. 

/models also includes:

- `proxy_models.pkl` - Pre-trained models to generate memorability features
- `training_statistics.pkl` - Statistics for feature standardization

## Quick Start

The notebook contains demonstrations of the following:

- Recognition predictions using the embedded model
- Recall predictions using the embedded model
- Recognition predictions using the proxy factors model given the slogan and brand information
- Recognition predictions using the proxy factors model given only the slogan
- Recall predictions using the proxy factors model

## Input Data Format

A .csv file of the slogans under consideration is required, one slogan per row.

The user specifies the column of the csv file that contain the slogan and the column that contains text representing the brand.






