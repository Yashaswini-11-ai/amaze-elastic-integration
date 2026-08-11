# HTTPJSON Configuration

## Endpoint

{{base_url}}/tickets

## Method

GET

## Authentication

API Key

## Polling Interval

5m

## Response Processing

AMaze API
      ↓
HTTPJSON Input
      ↓
Ingest Pipeline
      ↓
ECS Mapping
      ↓
Elastic Data Stream