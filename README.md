# App4htmlVisualinR

**App4htmlVisualinR** is an R/Shiny web application for organizing, generating, displaying, and sharing HTML-based R visualizations. It helps researchers convert structured CSV input or pasted R visualization scripts into browser-viewable outputs without requiring all users to work directly in a local R environment.

## Purpose

R is widely used for statistical analysis and visualization, but many outputs remain confined to local R sessions or static image files. App4htmlVisualinR provides a browser-based workflow for generating reader-oriented HTML visualizations from built-in examples, editable CSV data, or pasted R scripts.

## Main Features

* Browser-based R/Shiny interface
* Built-in visualization examples with editable input data
* CSV-formatted input guidance for different plot types
* Choropleth maps for Taiwan, world, United States, and China
* World bubble dashboard with optional relation curves
* Additional plots, including calendar heatmap, Sankey diagram, network plot, chord diagram, donut plot, lollipop chart, slopegraph, forest plot, and related visualizations
* Custom R plot mode for pasted R scripts
* Downloadable HTML outputs for sharing with collaborators, readers, or supplementary materials

## Visualization Routes

### Route A: Geographic Maps

Users can generate choropleth maps by entering region-level values in CSV format. The world map also supports a bubble-dashboard mode when a cluster column is provided.

Example input:

```csv
Country,count
Taiwan,233
Japan,116
USA,238
UK,81
India,102
```

For relation curves between countries, use edge-list data:

```csv
term1,term2,WCD
USA,Taiwan,8
USA,UK,5
Taiwan,Japan,6
India,UK,3
```

The relation-curve checkbox must be selected to display geographic connections.

### Route B: Additional Plots

The Additional plots module supports multiple visualization types using simple CSV input. If the input box is left blank, the app can insert built-in example data for the selected plot type.

Examples of supported formats include:

```csv
Age,Female,Male
0-4,120,130
5-9,110,115
10-14,100,105
```

```csv
source,target,value
Agricultural,Bio-conversion,124.73
Bio-conversion,Liquid,0.597
Bio-conversion,Losses,26.862
```

```csv
date,value
2012-01-01,23.45
2012-01-02,22.97
2012-01-03,24.11
```

### Route C: Custom R Plot

Users can paste an R script and select **Run pasted R script only**. The app executes the pasted script, captures the resulting visualization, and embeds it in an HTML output.

This route is useful when users already have working R visualization code and want to convert the result into a shareable browser-based file.

## Installation

Install R and RStudio first, then install the required packages:

```r
install.packages(c(
  "shiny",
  "readr",
  "dplyr",
  "reshape2",
  "Matrix",
  "DT",
  "ggplot2",
  "visNetwork",
  "htmltools",
  "htmlwidgets"
), dependencies = TRUE)
```

Additional packages may be required depending on the selected visualization or pasted R script.

## Running the Application Locally

Clone or download this repository, then run:

```r
shiny::runApp()
```

Or open `app.R` in RStudio and click **Run App**.

## Deployment

The application can be deployed to a Shiny-compatible server such as shinyapps.io.

```r
install.packages("rsconnect")

rsconnect::setAccountInfo(
  name = "your_account_name",
  token = "your_token",
  secret = "your_secret"
)

rsconnect::deployApp()
```

Replace the account name, token, and secret with your own shinyapps.io information.

## Required Environment

* R version 4.0.0 or later
* RStudio or another R-compatible development environment
* Windows, macOS, or Linux
* Modern web browser, such as Chrome, Edge, Firefox, or Safari
* Shiny-compatible hosting service for online deployment

## Dependencies

Core dependencies include:

* `shiny`
* `readr`
* `dplyr`
* `reshape2`
* `Matrix`
* `DT`
* `ggplot2`
* `visNetwork`
* `htmltools`
* `htmlwidgets`

Optional packages may be needed for specific plots, maps, Sankey diagrams, chord diagrams, calendar heatmaps, or custom pasted scripts.

## Example Applications

The manuscript demonstrates four example outputs:

1. Worldwide choropleth map
2. World bubble dashboard with relation curves
3. Calendar heatmap using VIX closing-value data
4. Energy-flow Sankey diagram

These examples show how App4htmlVisualinR converts structured input data or pasted R scripts into browser-viewable HTML visualizations.

## Output

The app produces downloadable HTML files that can be shared with collaborators, readers, or uploaded as supplementary web materials. This allows users to distribute interactive or browser-viewable visualizations without requiring recipients to run R code locally.

## Limitations

Custom pasted R scripts may fail if required packages, local files, system dependencies, or fonts are unavailable in the deployed Shiny environment. Users should simplify scripts, avoid local file paths, and ensure all required packages are installed before deployment.

## Citation

If you use App4htmlVisualinR in academic work, please cite the associated manuscript:

> App4htmlVisualinR: An R/Shiny Web Application for Organizing, Displaying, and Sharing HTML-Based R Visualizations.

## License

Please specify the license for this repository, such as MIT, GPL-3, or another open-source license.

## Contact

For questions, suggestions, or bug reports, please open an issue in this GitHub repository or contact the project maintainer.
