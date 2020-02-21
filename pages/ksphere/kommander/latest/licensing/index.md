---
layout: layout.pug
navigationTitle: Licensing
title: Licensing
excerpt:
menuWeight: 6
---

## Licensing

Kommander requires a valid license to continue use beyond adding a second cluster. A license can be generated from the [support portal][support_downloads] after [logging in][support_login] or by reaching out to your sales rep. Once downloaded, an admin user can add your license key to the Administration / Licensing section of Kommander.

Under the hood, a license consists of a License custom resource object that references a secret containing the actual license text.

Clicking + Add License takes you to the license form where a license can be created by adding the license to the textarea.

![Licenses Form](/ksphere/kommander/img/Licenses-form.png)

Licenses Form

If there is an error submitting the license, the error banner contains directions on how to add the license directly through kubectl.

![Licenses Error](/ksphere/kommander/img/Licenses-error.png)

Licenses Error

[support_downloads]: https://support.d2iq.com/s/downloads
[support_login]: https://support.d2iq.com/s/login/
