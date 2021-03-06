# restic with MinIO Server [![Slack](https://slack.min.io/slack?type=svg)](https://slack.min.io)

`restic` is a fast, efficient and secure backup tool. It is an open source project available under ``BSD 2-Clause License``.

In this recipe we will learn how to use `restic` to backup data into MinIO Server.

## 1. Prerequisites

Install MinIO Server from [here](https://docs.min.io/docs/minio-quickstart-guide).

## 2. Installation

Install restic from [https://restic.github.io](https://restic.github.io).

## 3. Configuration

Set MinIO credentials in the environment variables as shown below.

```sh
export AWS_ACCESS_KEY_ID=<YOUR-ACCESS-KEY-ID>
export AWS_SECRET_ACCESS_KEY= <YOUR-SECRET-ACCESS-KEY>
```

## 4. Commands

Start `restic` and point it to the bucket where the backup data will reside.

```sh
./restic -r s3:http://localhost:9000/resticbucket init
```

Copy backups from the local machine to the bucket on MinIO server.  

```sh
./restic -r s3:http://localhost:9000/resticbucket backup /home/minio/workdir/Docs/
enter password for repository:
scan [/home/minio/workdir/Docs]
scanned 2 directories, 6 files in 0:00
[0:00] 100.00%  0B/s  8.045 KiB / 8.045 KiB  6 / 8 items  0 errors  ETA 0:00
duration: 0:00, 0.06MiB/s
snapshot 85a9731a saved
```
