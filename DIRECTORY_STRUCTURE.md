# Lending App – Detailed Directory Structure

**Path:** `arcane-bench/apps/lending/`

---

## Root (apps/lending/)

```
lending/
├── .editorconfig
├── .flake8
├── .gitignore
├── .mergify.yml
├── .pre-commit-config.yaml
├── .releaserc
├── codecov.yml
├── CODE_OF_CONDUCT.md
├── CODEOWNERS
├── commitlint.config.js
├── crowdin.yml
├── license.txt
├── MANIFEST.in
├── pyproject.toml
├── README.md
├── setup.py
├── sider.yml
│
├── .github/
│   ├── helper/
│   │   ├── install.sh
│   │   ├── site_config.json
│   │   ├── translation.py
│   │   └── update_pot_file.sh
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.yaml
│   │   ├── config.yml
│   │   └── feature_request.yaml
│   ├── labeler.yml
│   ├── lending-hero.png
│   ├── lending-logo.png
│   ├── PULL_REQUEST_TEMPLATE.md
│   └── workflows/
│       ├── ci.yml
│       ├── generate-pot-file.yml
│       ├── initiate_release.yml
│       ├── labeller.yml
│       ├── linters.yml
│       ├── on_release.yml
│       └── release_notes.yml
│
└── lending/                          # Main app package
```

---

## Main App Package: lending/lending/

```
lending/lending/
├── __init__.py
├── hooks.py
├── install.py
├── utils.py
├── modules.txt
├── patches.txt
│
├── config/
│   └── __init__.py
│
├── desktop_icon/
│   └── lending.json
│
├── fixtures/
│   ├── role.json
│   ├── workflow.json
│   ├── workflow_action_master.json
│   └── workflow_state.json
│
├── locale/                            # Gettext translations (.po/.pot)
│   ├── main.pot
│   ├── ar.po, bs.po, cs.po, da.po, de.po, eo.po, es.po, fa.po, fr.po
│   ├── hr.po, hu.po, id.po, it.po, my.po, nb.po, nl.po, pl.po
│   ├── pt.po, pt_BR.po, ru.po, sr.po, sr_CS.po, sl.po, sv.po
│   ├── ta.po, th.po, tr.po, vi.po, zh.po
│   └── ... (other locale files)
│
├── overrides/                         # Frappe/ERPNext overrides
│   ├── __init__.py
│   ├── company.py
│   ├── custom_field.py
│   ├── gl_entry.py
│   └── sales_invoice.py
│
├── patches/                           # Database/schema migration patches
│   ├── v1_0/
│   │   ├── add_index_for_custom_fields_for_JE.py
│   │   ├── create_custom_field_loan_accrual_rate_for_company.py
│   │   ├── fix_invalid_loan_product_values.py
│   │   ├── rename_is_accrued_to_demand_generated.py
│   │   ├── update_value_date_in_loan_refund.py
│   │   ├── update_value_date_in_loan_repayment.py
│   │   └── update_value_date_in_pending_doctypes.py
│   ├── v15_0/
│   │   ├── add_loan_product_code_and_rename_loan_name.py
│   │   ├── create_accounting_dimensions_for_loan_doctypes.py
│   │   ├── create_custom_field_for_bpi.py
│   │   ├── create_custom_field_for_collection_offset_sequence_*.py
│   │   ├── create_custom_field_for_interest_day_count_convention.py
│   │   ├── create_custom_field_for_irac_provisioning_configuration.py
│   │   ├── create_custom_fields.py
│   │   ├── fix_typo_in_irac_provisioning_configuration.py
│   │   ├── generate_loan_classifications_from_loan_asset_classification_ranges.py
│   │   ├── generate_loan_repayment_schedule.py
│   │   ├── loan_disbursement_status_patch.py
│   │   ├── loan_interest_accrual_changes.py
│   │   ├── loan_repayment_schedule_status_patch.py
│   │   ├── make_loan_type_non_submittable.py
│   │   ├── migrate_loan_type_to_loan_product.py
│   │   ├── rename_*.py (multiple)
│   │   ├── update_classification_fields_in_loan.py
│   │   ├── update_company_loan_asset_classification_ranges_table.py
│   │   ├── update_custom_fields_for_company_tab.py
│   │   ├── update_loan_asset_classification_ranges.py
│   │   ├── update_loan_column_break_due_to_bpi.py
│   │   ├── update_loan_product_accounts.py
│   │   ├── update_loan_security_assignment_pledge_status.py
│   │   ├── update_loan_types.py
│   │   ├── update_maturity_date.py
│   │   └── update_min_bpi_application_days.py
│   └── v16_0/
│       └── add_enable_loan_accounting_field.py
│
├── public/
│   ├── .gitkeep
│   ├── dist/
│   │   └── js/
│   │       ├── lending.bundle.*.js
│   │       └── lending.bundle.*.js.map
│   ├── icons/
│   │   ├── frappe-lending-logo.svg
│   │   └── desktop_icons/
│   │       ├── solid/
│   │       │   └── frappe-lending-logo.svg
│   │       └── subtle/
│   │           └── frappe-lending-logo.svg
│   ├── images/
│   │   └── frappe-lending-logo.svg
│   └── js/
│       ├── lending.bundle.js
│       ├── custom_customer.js
│       └── loan_common.js
│
├── templates/
│   └── pages/
│       └── __init__.py
│
├── tests/
│   └── test_utils.py
│
├── translations/                      # CSV translations (64 locale files)
│   └── af.csv, am.csv, ar.csv, bg.csv, bn.csv, ... zh.csv, zh-TW.csv
│
├── workspace/
│   └── lending.json
│
├── loan_origination/                  # Loan origination sub-module
└── loan_management/                   # Loan management sub-module
```

---

## loan_origination/

```
lending/lending/loan_origination/
├── __init__.py
│
├── dashboard_chart/
│   ├── applications/
│   │   └── applications.json
│   └── loan_application_statuses/
│       └── loan_application_statuses.json
│
└── doctype/
    ├── __init__.py
    ├── loan_application_document/
    │   ├── __init__.py
    │   ├── loan_application_document.json
    │   └── loan_application_document.py
    ├── loan_co_applicants/
    │   ├── __init__.py
    │   ├── loan_co_applicants.json
    │   └── loan_co_applicants.py
    ├── loan_document_type/
    │   ├── __init__.py
    │   ├── loan_document_type.json
    │   ├── loan_document_type.js
    │   ├── loan_document_type.py
    │   └── test_loan_document_type.py
    └── loan_origination_settings/
        ├── __init__.py
        ├── loan_origination_settings.json
        ├── loan_origination_settings.js
        ├── loan_origination_settings.py
        └── test_loan_origination_settings.py
```

---

## loan_management/

```
lending/lending/loan_management/
├── controllers/
│   └── loan_controller.py
│
├── dashboard_chart/
│   ├── loan_disbursements/
│   │   └── loan_disbursements.json
│   ├── loan_interest_accrual/
│   │   └── loan_interest_accrual.json
│   ├── new_loans/
│   │   └── new_loans.json
│   └── top_10_pledged_loan_securities/
│       └── top_10_pledged_loan_securities.json
│
├── dashboard_chart_source/
│   ├── __init__.py
│   └── top_10_pledged_loan_securities/
│       ├── __init__.py
│       ├── top_10_pledged_loan_securities.json
│       ├── top_10_pledged_loan_securities.js
│       └── top_10_pledged_loan_securities.py
│
├── doctype/                           # All DocTypes (see below)
├── loan_management_dashboard/
│   └── loan_dashboard/
│       └── loan_dashboard.json
│
├── number_card/
│   ├── active_loans/          → active_loans.json
│   ├── active_securities/     → active_securities.json
│   ├── applicants_with_unpaid_shortfall/ → applicants_with_unpaid_shortfall.json
│   ├── closed_loans/           → closed_loans.json
│   ├── last_interest_accrual/  → last_interest_accrual.json
│   ├── new_loan_applications/ → new_loan_applications.json
│   ├── new_loans/              → new_loans.json
│   ├── open_loan_applications/ → open_loan_applications.json
│   ├── total_disbursed/        → total_disbursed.json
│   ├── total_repayment/       → total_repayment.json
│   ├── total_sanctioned_amount/ → total_sanctioned_amount.json
│   ├── total_shortfall_amount/  → total_shortfall_amount.json
│   └── total_write_off/       → total_write_off.json
│
├── report/
│   ├── __init__.py
│   ├── alm_audit_report/       (.json, .js, .py)
│   ├── applicant_wise_loan_security_exposure/
│   ├── future_cashflow_report/
│   ├── loan_outstanding_report/
│   ├── loan_repayment_and_closure/
│   ├── loan_security_exposure/
│   ├── loan_security_status/
│   └── past_cashflow_report/
│
└── workspace/
    └── lending/
        └── lending.json
```

---

## loan_management/doctype/ (DocTypes)

Each DocType folder typically contains: `__init__.py`, `*.json`, `*.py`, and often `*.js`, `*_dashboard.py`, `test_*.py`, `*_list.js`, `utils.py`.

| DocType | Notes |
|---------|--------|
| bulk_repayment_log | dashboard, tests |
| co_lender_schedule | |
| days_past_due_log | |
| loan | main loan doctype; list, dashboard |
| loan_accrual_repost | + detail child |
| loan_accrual_repost_detail | child |
| loan_adjustment | + detail child, dashboard |
| loan_adjustment_detail | child |
| loan_application | dashboard |
| loan_balance_adjustment | |
| loan_category | |
| loan_charge_reference | |
| loan_charges | |
| loan_classification | |
| loan_classification_range | |
| loan_demand | |
| loan_demand_offset_detail | child |
| loan_demand_offset_order | |
| loan_disbursement | dashboard, list, tests |
| loan_disbursement_charge | child |
| loan_freeze_log | |
| loan_interest_accrual | |
| loan_irac_provisioning_configuration | |
| loan_limit_change_log | |
| loan_npa_log | |
| loan_partner | dashboard, tests |
| loan_partner_address | child |
| loan_partner_adhoc_charges_shared | |
| loan_partner_shareable | |
| loan_product | dashboard, tests |
| loan_product_loan_partner | child |
| loan_refund | |
| loan_repayment | dashboard, utils |
| loan_repayment_charges | |
| loan_repayment_detail | child |
| loan_repayment_repost | + cancel/detail children |
| loan_repayment_repost_cancel_detail | child |
| loan_repayment_repost_detail | child |
| loan_repayment_schedule | list, utils, tests |
| loan_restructure | dashboard, list |
| loan_restructure_limit_log | |
| loan_security | dashboard |
| loan_security_assignment | list, tests |
| loan_security_deposit | |
| loan_security_price | |
| loan_security_release | list, tests |
| loan_security_shortfall | |
| loan_security_type | dashboard |
| loan_transfer | dashboard |
| loan_transfer_detail | child |
| loan_write_off | |
| pledge | |
| prepayment_charges | |
| process_loan_classification | |
| process_loan_demand | dashboard |
| process_loan_interest_accrual | dashboard |
| process_loan_interest_change | |
| process_loan_restructure_limit | |
| process_loan_security_shortfall | |
| proposed_pledge | |
| repayment_schedule | |
| sanctioned_loan_amount | |
| unpledge | |

---

## Summary

| Section | Description |
|--------|-------------|
| **Root** | Config, CI/CD (`.github`), code quality, packaging (`setup.py`, `pyproject.toml`). |
| **lending/** | App entry: `hooks`, `install`, `utils`, `config`, `fixtures`, `overrides`, `patches`, `public`, `templates`, `tests`, `translations`, `workspace`. |
| **loan_origination** | DocTypes and dashboard charts for application, co-applicants, documents, settings. |
| **loan_management** | Controllers, dashboard charts/sources, **~55 DocTypes**, number cards, **8 reports**, workspace, loan dashboard. |
| **locale / translations** | Gettext (`.po`/`.pot`) and CSV translations for many languages. |

*Generated from `arcane-bench/apps/lending`.*
