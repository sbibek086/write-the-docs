---
layout: default
title: what compiler is trying to say Explained
category: Programming
tags: [Programming]
---
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/dc31d0e2-d234-4575-9827-c3c52d09d9cd)

restart runtime message reading:
there might be dependency conflict <- sthg like that message 
when I try to run 
import cudf
codeblock confused killed me about from where to restart runtime to clean slate n then again-put local variables.

It turns out
I dont have to restart all the way from 
apt-get update
apt-get install nvidia-cuda-toolkit
but JUST RESTART
pip install cudf-cu11 --extra-index-url=https://pypi.nvidia.com
wala cell

lets understand why exactly that dependency conflict came?
So, apt-get update updates package list in my colab VM by fetching latest version of package list from repo n updates also local package cache.
n
apt ... cuda toolkit installs nvidia CUDA toolkit, which provides development env (dev env includes GPU accel libraries, compiler for nvidia gpu n runtime libraries) for creating high performance GPU accelerated applications.

~~~
Mind u that CUDA is parallel computing platform n programming model developed by nvidia, which allows developers to use nvidia gpu for general-purpose processing, enabling high-performance computing applications.
CUDA provides
-tools, 

-libraries (such as cuBLAS n cuFastFourierT to achieve high performance on gpu operations. n cuBLAS cuFFT libs are used by open source libs like cuPy in replacement for PyPI's NumPy), 

-runtime environment for executing programs on nvidia gpu. 

Long story short: CUDA serves as foundational framework that enables both cuPy and cuDF to leverage the computational power of NVIDIA GPUs. Without CUDA, these libraries would not be able to execute operations on GPUs. cuPy and cuDF are complementary in the sense that cuPy is advanced gpu-compatible cousin library to NumPy, n cuDataFrame to pandas. 
~~~
So, it must have been that when I was running 
pip install cudf-cu11 --extra-index-url=https://pypi.nvidia.com wala cell,
it must have been disturbed by packages or variables just-before-installed-by apt-get update n apt .. toolkit wala cell block
because similar packages n vars we are trying to install but specifically from cudf-cu11, so it is begging, "Restart session means Just rerun only this cell, IDIOT n not from the beginning"
Primer is on my blog: What does restart session n again running certain cell do on memory clearance n library re initialization, when to do it n why its necessary

---
After above problesm is solved, again this problem
![image](https://github.com/sbibek086/write-the-docs/assets/11883023/a8424527-9388-4f09-8c4a-10584f639b80)

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/2a473ef5-d1b3-4cbd-bb0c-d884a8dbeb65)

---
Compiler messages and their meanings explained:

pip's dependency resolver does not currently take into account all the packages that are installed.

means

this error means that when pip is installing or upgrading a package, it may not fully consider the versions of already installed packages. This can lead to version conflicts or the installation of incompatible versions, as pip doesn't re-evaluate all dependencies of all installed packages during this process.

The following packages were previously imported in this runtime:
  [cuda]

means

the listed packages, in this case, "cuda," have already been imported or loaded into the current runtime environment. This might indicate that the runtime environment has preloaded these packages, potentially affecting subsequent operations or dependencies that rely on them.

---
huge todo:

![image](https://github.com/sbibek086/write-the-docs/assets/11883023/cd0b2bea-eac3-472d-87c4-0451fc0aee0d)

---
Since I have big csv files reduced to parquets, below is not my headache now
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
