# Reference Multimodal Datalake

How do you work with 1,000,000 images? Or videos? Or documents? Also, what about all the associated metadata like
the date an image was taken? Or the height/width of each image? Or maybe annotations on the image?

Argh! Why is it so hard?

A Multimodal Data Warehouse needs to provide (in order of Data Warehousing exotic-ness):

1. **Running analytics (just like any good ol' Data Warehouse):** count how many images there are, grouped by the URL domain name
2. **Running multimodal operations:** extract the height/width of an image, or maybe calculate the CLIP embedding of an image
3. **Running (multimodal) LLMs... efficiently:** run the newest fancy open-sourced LLM model on all the available GPUs, or maybe make API calls to OpenAI's GPT-4o to prompt my models with my images
4. **Feed model training:** stream my data to a model training system (e.g. Pytorch running on GPU machines)
2. **Clustering algorithms:** cluster my documents based on some semantic similarity metric, and then deduplicate them

Traditional data warehouses (or a data lakehouse, if you're feeling fancy) really handle only (1) well. This repo shows an example of building an effective **Multimodal** data warehouse using nothing but [Daft](https://www.getdaft.io), good old Parquet files, and URLs pointing to files in AWS S3 (or any object store of your choice, really).

Along the way, we will showcase benchmarks and show how just this simple tried-and-true set of tools can go a *long* way, and still maintain interoperability with all the other really good open-source tooling such as DuckDB, Trino, Spark and more.
