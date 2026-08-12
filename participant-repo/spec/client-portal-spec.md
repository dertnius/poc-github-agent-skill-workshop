# Retail Client Portal — Account Opening & Payments — Requirements Specification

**Version:** 0.9 (DRAFT) · **Author:** J. Meier, Business Analyst · **Status:** For review

## 1. Purpose

This document specifies the requirements for the new Retail Client Portal (RCP-Web), covering digital account opening and client payment transactions for retail clients in Switzerland.

## 2. Scope

In scope: account opening for natural persons, domestic CHF and SEPA EUR payment orders. Out of scope: mortgages, securities trading, corporate clients.

## 3. Functional Requirements — Account Opening

**REQ-001** — When a client submits an account opening request, the system shall assign a unique application ID and display it to the client within 2 seconds.

**REQ-002** — The system shall verify the client's identity document, create the account master record, and send the welcome letter.

**REQ-003** — The client shall upload a copy of their identity document during onboarding.

**REQ-004** — The account currency shall be selected via a React dropdown component, implemented in TypeScript, populated from core banking table T_CURR.

**REQ-005** — While an account opening application is in status "Under Review", the system shall prevent the client from editing submitted data.

## 4. Functional Requirements — Payments

**REQ-006** — The system shall process most payment orders quickly.

**REQ-007** — Domestic payment orders below CHF 1,000 shall be executed immediately without additional authorization.

**REQ-008** — When a payment order is rejected by the compliance check, the system shall require the reviewing officer to record a rejection reason of at least 20 characters.

**REQ-009** — All payment orders, regardless of amount, shall require confirmation via second-factor authentication before execution.

## 5. Non-Functional Requirements

**REQ-010** — The system shall complete client login within 3 seconds for the 95th percentile of requests under a load of 500 concurrent sessions.

**REQ-011** — The e-banking interface shall be intuitive and user-friendly.

**REQ-012** — If a duplicate payment order (identical debtor IBAN, creditor IBAN, amount, and execution date) is submitted within 5 minutes, then the system shall reject it and display error message ERR-DUP-01.

---
*End of document. Please review and return comments to the author by Friday.*
