# Inventory Ledger Reconciliation

An open-source inventory and accounting reconciliation system with deterministic, traceable, and explainable matching rules.

## Overview

Inventory Ledger Reconciliation is a web application under development designed to reconcile inventory movements and accounting entries from independent data sources.

The system aims to identify matches, discrepancies, unmatched records, and ambiguous relationships while preserving the original source data and ensuring traceability throughout the reconciliation process.

## Core Principles

- Preserve original source data.
- Treat inventory and accounting data as independent sources.
- Reconcile records at the individual transaction level.
- Use deterministic and explainable reconciliation rules.
- Ensure traceability of reconciliation results.
- Never resolve ambiguous matches arbitrarily.
- Never modify records in source systems.
- Use synthetic data for development and testing.

## Initial MVP Scope

The preliminary scope includes:

- Importing inventory and accounting data from CSV and Excel files.
- One-to-one reconciliation.
- Identification of matched records.
- Identification of value discrepancies.
- Identification of unmatched inventory records.
- Identification of unmatched accounting records.
- Identification of ambiguous matches.

The final MVP requirements will be established during domain modeling.

## Out of Initial Scope

- ERP integrations.
- User authentication.
- Advanced reconciliation history.
- One-to-many, many-to-one, and many-to-many reconciliation.
- Automatic corrections in source systems.

## Project Status

This project is in its initial development stage.

Domain requirements, software architecture, and technology stack have not yet been finalized.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.