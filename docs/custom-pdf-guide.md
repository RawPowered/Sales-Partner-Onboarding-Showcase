# Custom PDFs and acknowledgement receipts

## Start with the right document

The optional PDF is a **public, company-wide document that applicants read**. The plugin does not fill, sign, stamp, or modify the PDF. Applicants enter their details and typed acknowledgement in a separate WordPress form. The plugin stores that form's receipt privately.

The included [free generic templates](../resources/document-templates/README.md) are blank starting points, with editable Markdown sources and ready-to-download PDFs.

**These generic templates have not been reviewed by a legal representative. They are not legal advice or production-ready agreements. Have a qualified legal representative review and adapt them for your organization and jurisdiction before live production use.**

The warning appears in the templates as well as this documentation. A free reuse license does not imply legal review, suitability, or enforceability.

## What the feature supports

| Item | Behavior |
| --- | --- |
| Document | One configured PDF per site at a time, shared by all application roles |
| Location | Local WordPress Media Library file, inside this site's uploads directory |
| Size/type | Up to 10 MB; PDF attachment MIME type, `.pdf` extension, and PDF file header are checked |
| URL | Host must match the WordPress site host; remote/CDN/offloaded-only files are not supported |
| Version | An administrator enters an explicit approved version |
| Integrity | SHA-256 records the configured file's bytes and detects changes |
| Applicant action | Read PDF, complete required details, acknowledge seven commitments, type matching legal name/signature, accept document and privacy consent |
| Receipt | Private WordPress application metadata, visible to authorized administrators |
| Identity | No email verification or independent identity verification |
| Signature output | Typed acknowledgement in the private record; no signed PDF is generated |
| Access | Submission, review approval, and course completion do not create an account or grant permissions |

The feature is optional and disabled by default. There are no per-role PDF assignments, multiple-document signing flows, uploaded applicant PDFs, signature images, or signing-provider integrations in this version.

## Prepare your own PDF

1. Copy a generic template or start with your own organization-approved document.
2. Replace every placeholder with reviewed company-wide content. The PDF is public, so do not put an applicant's name, address, signature, completed application, credentials, or other confidential material in it.
3. Review the seven fixed form commitments listed below. Changing words in a PDF does **not** change those form checkboxes. If your approved document conflicts with them, keep the requirement off until the wording and workflow have been reconciled.
4. Have your legal representative review the completed document and its intended acknowledgement process before live production use. Also review company-specific retention and privacy arrangements.
5. Export a normal, unencrypted PDF. The plugin's basic PDF checks do not certify readability, accessibility, legal validity, or document safety. Open the actual file and test its links/readability before uploading it.
6. Put a visible version identifier in the PDF, such as `company-onboarding-2026-01`, and retain that exact original in your organization's document archive.

Do not publish the supplied blank worksheets as final company terms. They deliberately contain no ready-made compensation agreement, employment/contractor classification, restrictive covenant, waiver, or jurisdiction-specific contract language.

## Configure it in WordPress

1. Open **Media → Add Media File** and upload the reviewed PDF. Keep the local file in WordPress uploads.
2. Open the attachment details. The numeric attachment ID appears in the WordPress admin address, for example `post=123` or `item=123`. Use `123`, not the file URL.
3. Open **Partner applications → Settings**.
4. Enter that number in **Agreement PDF attachment ID** and the reviewed identifier in **Approved agreement version**.
5. Check **Require agreement acknowledgement and all partner commitments**. Ensure your company identity and privacy notice are configured. Save settings.
6. If validation fails, WordPress displays a settings error and closes intake. Correct the file/version, deliberately re-enable **Accept new applications**, and save again.
7. Open the public onboarding page. Check the exact PDF link/version, required legal-name/address fields, seven commitments, matching typed signature, and acknowledgement text. Use clearly labeled synthetic details in a test installation first.
8. Confirm the private administrator receipt contains the expected version and hash. Notifications are a separate setting and do not verify an applicant's identity.

## What applicants acknowledge

When the PDF requirement is enabled, the form additionally requires:

- Business or team name, full legal name, mailing address, and a typed signature matching that legal name exactly.
- All seven fixed commitments: limits on authority; no unapproved promises; no side deals; customer permission and approved information channels; reporting duties; conduct/access consequences; and electronic acknowledgement/record retention.
- The acknowledgement shown below, plus the ordinary privacy/contact consent.

The current document acknowledgement reads:

> I reviewed the agreement and confirm that my details are accurate. This acknowledgement does not establish compensation, exclusivity, appointment, or account access by itself.

Applicants enter their own information in WordPress. The uploaded PDF remains the same public template for every applicant. Required legal-name fields are textual; the plugin does not verify identity or whether a person had authority to act for a business.

## What is stored

An accepted application is saved privately before an optional administrator notification is attempted. Its data/receipt include:

- Applicant details and typed signature, the selected role's name and format at submission, and each accepted commitment flag.
- UTC submission timestamp, company name, privacy notice URL, and exact consent/acknowledgement/commitment wording.
- PDF attachment ID, URL, approved version, and SHA-256 file hash.
- Submission identifier for duplicate protection and separate administrator review history.

Administrators review these under **Partner applications**. Receipt fields are displayed as evidence rather than editable application text. Later role renaming does not rewrite earlier role wording. The plugin does not claim cryptographic signer identity, tamper-proof storage, immutable PDF archiving, legal enforceability, or a third-party signing certificate.

## Update, replace, or disable a document

- **New document bytes need a new approved version.** Upload a new attachment rather than replacing the old file in place, archive the original, enter a new version, and save.
- If a configured file is changed without approval, new submissions are blocked. A form already open in a browser also fails if its document hash no longer matches; the applicant must refresh and review the current document.
- Saving different bytes under the same approved version is rejected and closes intake. Correct the version/file, re-enable applications deliberately, and save.
- Deleting or making a required file unreadable blocks new acknowledgements. Restore the reviewed file or configure a new approved document/version.
- Unchecking the PDF requirement allows ordinary intake without new agreement fields. Existing receipts remain stored. Do not treat new applications as having acknowledged a prior document.
- Turning the requirement on later does not retroactively add acknowledgements to existing applications.
- A single configured document applies to all roles. To vary terms, prepare a reviewed company-wide document that clearly identifies applicable sections; the plugin does not choose a different PDF for each role.

The plugin records hashes but does not retain immutable copies of every version. Keep old approved originals and their version/hash records in your own archive so earlier receipts remain interpretable.

## Privacy, retention, and recovery

The Media Library template is public; private receipt storage does not make the PDF confidential. Application pages use no-cache/noindex directives, but **noindex is not access control for an uploaded PDF**. Verify public file access contains only intended company-wide content.

Deactivation and plugin removal preserve applications and settings. WordPress privacy export includes matching receipts; privacy erasure retains applications/acknowledgements pending administrator retention review. Establish a reviewed retention policy and database/document backups before real intake.

For problems, first close new applications and preserve existing evidence. Check the attachment ID, local file availability, host, size, PDF header, version, and changed file bytes. Refresh a stale form after the configuration is repaired. Never manually alter an earlier receipt to make it appear to acknowledge a different document.
