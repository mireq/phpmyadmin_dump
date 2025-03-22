# PHPMyAdmin Database Dump Script

This is a simple Python script to dump a database from PHPMyAdmin.

## Requirements

- Python 3.x
- `requests` library
- `lxml` library

## Installation

Install the required libraries using pip:

```sh
pip install requests lxml
```

## Usage

```sh
python phpmyadmin_dump <url> <username> <password> [--timeout TIMEOUT] [--databases DATABASES] [--output_dir OUTPUT_DIR]
```

- `url`: The URL of the PHPMyAdmin page.
- `username`: The username of the database.
- `password`: The password of the database.
- `--timeout`: Request timeout (default: 60 seconds).
- `--databases`: List of databases to dump (default: all databases).
- `--output_dir`: Output directory (default: current directory).

## Example

```sh
python phpmyadmin_dump.py http://localhost/phpmyadmin user pass --databases db1 db2 --output_dir /path/to/output
