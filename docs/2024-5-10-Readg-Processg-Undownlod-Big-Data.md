---
layout: default
title: ..
category: ML
tags: [ML]
---

Undownloadable Big csv files are killing me. My next step of converting it to training_batch, testing_batch parquet has been roadblocked.

Lets see what I have found so far:

[This reddit thread](https://www.reddit.com/r/datascience/comments/xwd6j5/working_with_more_than_10gb_csv/) didnt help much.

But since I will soon have colab Pro+.
Lets explore Google Colab Pro+ with Google Cloud Storage (GCS) n other Google Cloud Platform (GCP) services, lets see below way:

gpt quotes from below,

Colab Pro+ provides increased RAM and storage compared to the free version, making it suitable for working with larger datasets. 

You can leverage this additional resources along with GCP services to process large CSV files without downloading them to your local machine.

Here's a general approach:

a) Upload CSV File to Google Cloud Storage (GCS): Upload your large CSV file to a GCS bucket. You can do this manually through the Google Cloud Console
or programmatically using the Google Cloud Storage Python client library.

b) [Data Processing with Google Cloud Dataproc or Dataflow](https://youtu.be/gT6lXKLOgj8): Google Cloud Dataproc is a managed Apache Spark and Apache Hadoop service that simplifies running big data processing workloads. 
Google Cloud Dataflow is a fully managed service for stream and batch processing. You can create a Dataproc cluster or Dataflow job to read the CSV file from GCS, process it, and write the result to another location.

c) Convert CSV to Parquet: Within the Dataproc cluster or Dataflow job, you can use Apache Spark or Apache Beam to read the CSV data, 
perform any necessary transformations or analyses, and then write the processed data to Parquet format. 

<script src="https://gist.github.com/sbibek086/f6e41a7fa7d501fc4555de68808a6e72.js"></script>

You'll need to set up authentication for Google Cloud Storage and Spark on Colab, and ensure that you have the necessary permissions to access GCS buckets. 
Additionally, you may incur costs associated with using Google Cloud Platform services, so be mindful of that when working with large datasets.

This approach allows you to handle large datasets without downloading them to your local machine, leveraging the resources and scalability of Google Cloud Platform services
like GCS, Dataproc, and Dataflow.
