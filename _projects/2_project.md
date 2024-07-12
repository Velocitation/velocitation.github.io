---
layout: page
title: Data Reporting Infrastructure Development
description: A robust tool for summarizing and analyzing scientific data for regulatory reporting
img: assets/img/dart.png
importance: 2
category: work
giscus_comments: false
---

## Overview

This project involves the development of a sophisticated data reporting infrastructure using Visual Basic. The tool is designed to ingest, process, and summarize both external analytical data reports from various laboratories and internal reports. Its primary function is to compile individual replicate measurements and generate comprehensive statistical reports, crucial for regulatory compliance in scientific research.

<div class="row justify-content-center">
    <div class="col-sm-8 mt-3 mt-md-0 d-flex justify-content-center">
        {% include figure.liquid loading="eager" path="assets/img/dartdiag.jpg" title="Levy-Jennings plot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: A high-level data flow diagram of the reporting infrastructure. Right: A sanitized sample of the tool's report output.
</div>

## Key Features

1. **Data Ingestion and Integration**: The tool seamlessly integrates data from multiple sources, including external laboratory reports and internal datasets, ensuring a comprehensive analysis.

2. **Automated Data Transposition**: Implements sophisticated algorithms to automatically transpose data into the required format for analysis and reporting.

3. **Statistical Analysis**: Performs complex statistical calculations, including averages, standard deviations, and determinations on a per nicotine basis.

4. **Comparative Analysis**: Calculates percentage reductions compared to reference products, providing crucial insights for regulatory reporting.

5. **Regulatory Compliance**: Incorporates specific rounding rules and Limit of Quantitation (LOQ) evaluations to ensure compliance with regulatory standards.

6. **Report Generation**: Automatically generates detailed summary reports, significantly reducing manual effort and potential for human error.

## Technical Details

While the specific code cannot be shared due to confidentiality constraints, the tool leverages Visual Basic's robust capabilities for data manipulation and user interface design. Key technical aspects include:

- **Data Parsing**: Utilizes advanced string manipulation and regular expressions to extract relevant data from various report formats.
- **Array Manipulation**: Employs multi-dimensional arrays to efficiently store and process large datasets.
- **Statistical Functions**: Implements custom functions for complex statistical calculations, ensuring accuracy and consistency.
- **User Interface**: Features an intuitive interface for data import, processing control, and report generation.

Here's a conceptual snippet that illustrates the tool's approach to data processing:

```vb
Sub ProcessData(inputData As Variant)
    Dim processedData As New Collection

    ' Iterate through input data
    For Each dataPoint In inputData
        ' Apply LOQ evaluation
        If dataPoint < LOQ Then
            dataPoint = LOQ / 2
        End If

        ' Apply rounding rules
        dataPoint = Round(dataPoint, 2)

        ' Store processed data point
        processedData.Add dataPoint
    Next dataPoint

    ' Perform statistical analysis
    averageValue = CalculateAverage(processedData)
    standardDeviation = CalculateStandardDeviation(processedData)

    ' Generate report
    GenerateReport averageValue, standardDeviation
End Sub
```

This conceptual code demonstrates the general approach to data processing, including LOQ evaluation, rounding, and statistical analysis.

## Impact and Future Directions

The development of this data reporting infrastructure has significantly streamlined the process of preparing scientific data for regulatory reporting. Key impacts include:

1. **Efficiency**: Drastically reduced the time required for data compilation and report generation.
2. **Accuracy**: Minimized the risk of human error in data transposition and calculations.
3. **Consistency**: Ensured uniform application of statistical methods and regulatory standards across all reports.
4. **Scalability**: Designed to handle increasing volumes of data as research expands.

Future enhancements could include:

1. **Machine Learning Integration**: Implementing predictive analytics to forecast trends in scientific measurements.
2. **Cloud Integration**: Developing a cloud-based version for improved accessibility and real-time collaboration.
3. **Automated Data Retrieval**: Integrating direct connections to laboratory instruments for real-time data ingestion.

This project showcases my ability to develop complex, regulation-compliant software solutions that bridge the gap between raw scientific data and actionable regulatory reports. It demonstrates my skills in data processing, statistical analysis, and creating user-friendly interfaces for specialized scientific applications.
