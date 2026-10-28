# Kenya medicine recall and rapid alert data

Python scripts for collecting medicine recall and rapid alert information published by Kenya’s Pharmacy and Poisons Board (PPB). This repository contains historical data and scripts for collecting alert tables and linked PDFs.

This is a fork of [afiadata/ppb_recalls](https://github.com/afiadata/ppb_recalls). It is not an official PPB service, a complete live recall register, or a source of clinical advice. Check the current notice on the PPB website before making decisions.

## Repository contents

- `src/scrape_data.py` collects rapid alert table fields and writes a CSV.
- `src/download.py` finds and downloads linked rapid alert PDFs.
- Other scripts in `src/` handle recall tables, PDFs and product information.
- `data/` contains historical CSV and PDF outputs; `product_info.csv` is an existing output.

The rapid alert scripts are configured for 2018–2025. Coverage depends on the source pages and their structure; missing pages or failed requests can produce incomplete results.

## Getting started

Create and activate a Python virtual environment, then install dependencies from the repository root:

```bash
python -m venv .venv
python -m pip install -r requirements.txt
```

Retrieve rapid alert tables as `rapid_alerts.csv` in the current directory:

```bash
python src/scrape_data.py
```

Download linked rapid alert PDFs to `rapid_alerts_pdfs/`:

```bash
python src/download.py
```

These scripts access the PPB website. Run them responsibly, check applicable site terms and verify data and notices against the source. The default year range can be changed in each script.

## Limitations

- The scripts rely on the website’s HTML layout and may need updating if it changes.
- Requests can fail; output should not be assumed complete.
- `src/main.py` is a placeholder and does not run the collection pipeline.
- The dependency declarations in `pyproject.toml` and `requirements.txt` differ; they need consolidation and testing.
- Automated tests, consistent timeouts and a documented refresh process would improve reliability.

## Source

Published notices: [Pharmacy and Poisons Board of Kenya](https://web.pharmacyboardkenya.org/). Check original notices and applicable data-use terms before redistributing or relying on collected files.
