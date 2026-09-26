# Verify a KiteScribe Windows download

KiteScribe is Windows transcription and screen-text capture software developed by [Caymran Cummings](https://github.com/caymran) (Caymran Coral Cummings) at [FXBG Foundry](https://fxbgfoundry.com/).

This guide explains how to check a direct-download installer before running it. For the Microsoft Store edition, start from the [official KiteScribe website](https://kitescribe.ai/) and follow its Store link.

## 1. Choose an official release

Open the [KiteScribe release archive](https://github.com/FXBGFoundry/kitescribe-releases/releases). Read the release notes and download the installer and its matching SHA-256 checksum file from the same release. Do not compare an installer with a checksum from a different version.

Keep both files in a folder you can find. Leave the installer unopened while you check it.

## 2. Calculate the installer checksum

Open PowerShell in that folder. Replace the example filename with the exact filename you downloaded:

```powershell
Get-FileHash -LiteralPath '.\KiteScribe-UserSetup.msi' -Algorithm SHA256
```

Compare the full `Hash` value with the value in the published checksum file. Letter case does not matter; every hexadecimal character must otherwise match. If the values differ, stop and download the files again from the official release. A checksum match confirms that the file matches the published checksum; it does not independently establish who published it.

## 3. Inspect the digital signature

For a signed direct installer, check its signature separately:

```powershell
Get-AuthenticodeSignature -LiteralPath '.\KiteScribe-UserSetup.msi' |
    Format-List Status, StatusMessage, SignerCertificate
```

Check for a valid signature and inspect the signer details against the official release information. An unexpected publisher or invalid signature is a reason to stop and ask for support. Follow your organization's software approval process.

## 4. Keep verification evidence

For an organizational evaluation, retain the release URL, version, download date, checksum result, and signature result. Where provided, download the release's SBOM and security package for your reviewer. An SBOM is an inventory of software components; it is not a guarantee that a release has no vulnerabilities.

## Help and related documentation

- [KiteScribe support](https://kitescribe.ai/support/)
- [KiteScribe downloads](https://kitescribe.ai/downloads/)
- [Product overview and installation notes](../README.md)

## Command references

- [Microsoft: Get-FileHash](https://learn.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash)
- [Microsoft: Get-AuthenticodeSignature](https://learn.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature)
