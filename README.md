# PHPMyAdmin Database Dump Script

A simple Python script to automate the process of exporting (dumping) databases from a PHPMyAdmin instance using HTTP requests.

---

## 🧰 Requirements

- Python 3.x
- [`requests`](https://pypi.org/project/requests/) library
- [`lxml`](https://pypi.org/project/lxml/) library

Install dependencies via:

```bash
pip install requests lxml
```

---

## 🚀 Usage

```bash
python phpmyadmin_dump.py <url> <username> <password> [options]
```

### Positional Arguments

| Argument   | Description                     |
| ---------- | ------------------------------- |
| `url`      | The URL of the PHPMyAdmin page. |
| `username` | The username for the database.  |
| `password` | The password for the database.  |

### Optional Arguments

| Option               | Description                                                               |
| -------------------- | ------------------------------------------------------------------------- |
| `--timeout TIMEOUT`  | Request timeout in seconds (default: `60`).                               |
| `--databases DB ...` | One or more database names to export.                                     |
| `--output_dir DIR`   | Directory to save dump files. Cannot be used with `--output`.             |
| `--output FILE`      | Output file path for a single database. Only valid when exporting one DB. |
| `--progress`         | Show a progress bar while downloading.                                    |

---

## ✅ Examples

### Dump all databases with progress indicator:

```bash
python phpmyadmin_dump.py https://example.com/phpmyadmin user pass --progress
```

### Dump a specific database to a file:

```bash
python phpmyadmin_dump.py https://example.com/phpmyadmin user pass --databases mydb --output mydb.sql
```

### Dump multiple databases to a directory:

```bash
python phpmyadmin_dump.py https://example.com/phpmyadmin user pass --databases db1 db2 --output_dir dumps/
```

---

## ⚠️ Notes & Constraints

- `--output` cannot be used with `--output_dir`.
- `--output` requires exactly one database name specified via `--databases`.
- The script disables SSL verification by default (`verify=False`) for compatibility with self-signed certificates.
- The script mimics a browser session to log in and access the export form programmatically.

---

## 🐞 Troubleshooting

- **Login fails?** Double-check the URL and your credentials.
- **Empty or missing output?** Ensure the correct databases are specified and the PHPMyAdmin export feature is available.
- **Script crashes with an HTML error?** You may be hitting a page layout or token mismatch. Update PHPMyAdmin or inspect manually.

---

## 📄 License

This project is released under the MIT License.
