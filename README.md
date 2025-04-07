
# DougScore Dataset

DougScore Dataset is an R-based data project that extends [Doug DeMuro’s](https://www.youtube.com/channel/UCsqjHFMB_JYTaEnf_vmTNqg) vehicle scoring system into a fully functional, analysis-ready dataset and toolkit. It supports car search, comparison, visualization, and GPT-powered review generation using OpenAI's API. The goal is to create a modern, extensible version of datasets like `mtcars`, enriched with DougScore metrics and real-world specs. Here's a link to the original [DougScore Dataset](https://docs.google.com/spreadsheets/d/1HcFstlJdQMlMEWhbdKXZWdAzR5RFMtj3kywLQcgkGPw/edit?gid=0#gid=0).

## Features

- Fuzzy and partial search for cars by make, model, or year  
- Compare multiple cars on performance, practicality, and specs  
- Visualize DougScores, horsepower, fuel efficiency, and more  
- Generate summary paragraphs and comparisons in Doug DeMuro’s review style using GPT  
- Support for rotary engines, electric vehicles, and incomplete specifications  

## Dataset Overview

The core dataset `dougscore` includes:

- DougScore components: `weekend_score`, `daily_score`, `total_score`  
- Specs: `mpg`, `hp`, `displacement`, `transmission`, `fuel`, `cylinders`  
- Derived fields:  
  - `cylinders_numeric`: numeric-only version of `cylinders`  
  - `rotary_engine`: boolean flag indicating rotary-powered vehicles  
  - `car_id`: concatenation of `year`, `make`, and `model` for labeling  

## Core Functions

### Search and Filtering

- `search_cars(query, metric = NULL)`  
- `search_metric(query, metric)`  
- `filter_by(column, query)`  

### Comparison and Analysis

- `compare_cars(queries)`  
- `find_similar_cars(query)`  
- `compare_cars_llm(car1, car2)`  

### Summarization

- `get_car_summary_llm(query)`  
- `generate_doug_joke(query)`  

### Visualization

- `plot_comparison()`  
- `plot_metric_by_make()`  
- `plot_score_vs_spec()`  
- `plot_score_by_carplay()`  

## OpenAI Integration

To enable GPT-based functionality, set your API key in your `.Renviron` file:

```
OPENAI_API_KEY=your-api-key-here
```

The key is accessed via `Sys.getenv()` and is never stored in this repository.

## Requirements

- R 4.1 or later  
- Required packages: `tidyverse`, `recipes`, `glue`, `ggrepel`, `stringdist`, `httr`, `jsonlite`  

## Next Steps

- Convert this into an installable R package using `devtools`  
- Add function documentation and vignettes  
- Include a Shiny interface for interactive exploration  
- Enable batch LLM summaries and exportable reports  

This project is licensed under the [MIT License](LICENSE).
