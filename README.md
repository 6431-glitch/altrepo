# SeamlessReader · AltStore Classic

Official catalog: **https://6431-glitch.github.io/altrepo/source.json**

[Add this source](altstore://source?url=https%3A%2F%2F6431-glitch.github.io%2Faltrepo%2Fsource.json) in **AltStore Classic**. This is not an AltStore PAL marketplace.

## Installation
- [ ] Install AltStore Classic and AltServer using the [official instructions](https://faq.altstore.io/).
- [ ] Open AltStore → Sources → + and paste the catalog URL above.
- [ ] Install SeamlessReader; the catalog stays empty until the first verified IPA release is published.
- [ ] Follow AltStore's signing/refresh requirements for your Apple account. Some supported comic sources contain adult content.

## Publishing
- [x] GitHub Pages is configured for `main`, root `/`; merge the initial catalog setup to publish the source.
- [ ] Configure `ALTSTORE_PUBLISH_TOKEN` as an organization Actions secret shared with selected app repositories (or in each app’s release environment): a fine-grained token restricted to this repository with **Contents: Read and write**. GitHub Free does not expose organization secrets to private repositories; use repository/environment secrets in that case.
- [ ] Set `ALTSTORE_ENABLED=true` in that environment after the source is live.
- [ ] A verified merged release PR in SeamlessReader uploads to TestFlight, exports a second IPA from the same archive, then publishes here.
- [ ] For each new build, the publisher uploads `SeamlessReader.ipa` and `SHA256SUMS` to a draft release, verifies assets, publishes the release, then atomically updates `source.json` on `main`.
- [ ] Release tags use `v<version>-build.<build>`; existing public assets cannot be replaced. Failed catalog writes can be retried with the exact original IPA, or publish a fresh build through the release workflow.
- [ ] Source permissions are extracted from the app and extensions; versions are newest-first. No certificates, private keys or tokens belong in this repository.
- [ ] Test installation and updating on a real phone, including offline downloads, widgets and share-extension App Group behavior after AltStore re-signing.

## Maintenance
- [ ] Renew the publisher token before expiration; disabled publishing leaves TestFlight unchanged.
- [ ] Preserve published assets referenced by older catalog versions.
- [ ] CI removes temporary IPA exports and unpacked metadata directories, including failures; release downloads remain available.

References: [Source format](https://faq.altstore.io/developers/make-a-source) · [Updating apps](https://faq.altstore.io/developers/updating-apps).
