# Power BI - Apache Druid Integration

A simple and powerful way to connect Power BI to Apache Druid using a custom DAX script.

## Overview

This repository provides a ready-to-use DAX script that enables seamless integration between Power BI and Apache Druid. The script handles all the necessary configurations, including query formatting, error handling, and data transformation, making it easy to connect to your Druid instance and start analyzing your data.

## Features

- Simple configuration - only two things to modify:
  - Your Druid URL
  - Your SQL query
- Automatic query formatting and escaping
- Built-in error handling and retry mechanism
- Automatic data type conversion
- Support for large result sets
- Configurable timeout settings
- Cache support for better performance

## Prerequisites

- Power BI Desktop
- Access to an Apache Druid instance
- Valid Druid URL

## Quick Start

1. Open Power BI Desktop
2. Go to Get Data > Other > Blank Query
3. Open the Advanced Editor
4. Copy and paste the contents of `druid_connect.dax` into the editor
5. Modify only two things:
   - Set your `druid_url` (don't include a trailing slash)
   - Write your SQL query between the quotes
6. Click Done and start analyzing your data

## Configuration

The script is pre-configured with optimal settings. You only need to modify:

1. **Druid URL**:
   ```dax
   druid_url = https://<your_druid_url> // don't use / with last character
   ```

2. **Your Query**:
   ```sql
   SELECT 
       *
   FROM 
       "YOUR_TABLE"
   limit 1
   ```

### Default Settings (No Modification Required)

- `timeout`: 300000ms (5 minutes)
- `maxSubqueryRows`: 100000000
- `useCache`: Enabled
- `executionMode`: "ASYNC"

## Query Examples

Simple query:
```sql
SELECT * FROM "your-datasource" LIMIT 100
```

Time-based query:
```sql
SELECT * FROM "your-datasource" 
WHERE __time >= CURRENT_TIMESTAMP - INTERVAL '1' DAY
```

## Contributing

Feel free to submit issues and enhancement requests!

## License

This project is licensed under the MIT License - see the LICENSE file for details. 