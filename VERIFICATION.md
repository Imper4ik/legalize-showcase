# Verification record

Documentation prepared on **7 November 2026**. The checks below retain their
original dates and describe the reviewed working version, not a new production certification.

| Date | Scope | Observed result |
|---|---|---|
| 8 Oct 2026 | Full Linux/PostgreSQL suite after audit fixes | 1,927 passed, 193 subtests, 2 skipped; 85.00% Python coverage. |
| 8–9 Oct 2026 | Local UI review | 46 desktop and 12 mobile routes; repeat visual inspection of four changed screens at 1440 and 375 pixels. |
| 14 Oct 2026 | Encryption, key rotation, case validation, preproduction settings and release-script regressions | 60 passed, 11 subtests on Linux/PostgreSQL. Windows: 59 passed, one shell-dependent skip. |
| 14 Oct 2026 | Separate synthetic deployment | Docker build/startup; strict Django deployment checks, migration check, pip check and verified HTTPS/readiness passed. |
| 14 Oct 2026 | Malware scanning | Enabled ClamAV detected the standard EICAR test signature. |
| 14 Oct 2026 | Field validation | All 67 populated encrypted values in the synthetic seed passed. |
| 14 Oct 2026 | Backup and recovery | Encrypted backup uploaded to local S3-compatible storage, downloaded and restored into a newly created PostgreSQL database. Four clients, four cases, five documents, one email record, four MOS records and five file hashes matched; the disposable target was removed. |

The two full-suite skips were caused by missing Node.js and Git executables in
that Linux container. Corresponding checks were run separately on Windows.
They are disclosed rather than counted as successes in the Linux run.

## Boundaries of the evidence

- Counts describe dated runs, not a continuously updated GitHub status.
- The reviewed candidate included local changes. Each new commit/deployment needs its own CI and acceptance run.
- The HTTPS login scenario reached staff pages after MFA, but the complete export scenario was not signed off: its print-preview expectation needed correction.
- Recovery used fictional data and local S3-compatible storage. This does not certify a live database restore or recovery after losing the host.
- No external penetration test, complete WCAG audit, measured ROI, paying user count or workload capacity is claimed.
- OCR/MOS output requires review; official submission and legal accuracy across all case types were not certified.

The evidence supports technical demonstrations and continued pilot preparation.
Operational acceptance remains a separate step for a real installation.
