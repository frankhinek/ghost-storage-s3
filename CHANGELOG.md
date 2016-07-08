# Change Log
All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](http://semver.org/).

## [Unreleased]
### Added
- Restored the ability to specify an `assetHost` in the Ghost `config.js` file.

### Changed
- Forked [frankhinek/ghost-storage-s3](https://github.com/frankhinek/ghost-storage-s3) from [spanishdict/ghost-s3-compat](https://github.com/spanishdict/ghost-s3-compat)
- Changed module name from ghost-s3-compat to ghost-storage-s3
- Start following [SemVer](http://semver.org) properly.
- Changed installation steps in README to match guidance by Ghost Foundation
CTO and co-founder, Hannah Wolfe, in [this issue](https://github.com/spanishdict/ghost-s3-compat/issues/5).

### Fixed
- Use path-style URLs to construct the S3 endpoint images can be read from to
avoid certificate validation failures.  This is necessary because common bucket
naming can include one or more dots `(.)`, such as images.yourdomain.com. If you
a virtual-hosted–style URL https://images.yourdomain.com.s3.amazonaws.com would
fail a certificate validity check because AWS uses a *.s3.amazonaws.com wildcard
cert. The certificate would be deemed invalid because RFC2818 allows matching of
only a single domain for a given wild card character.

## [1.0.2] - 2016-04-20
### Changed
- Add support for proxying local image requests to S3

## [1.0.1] - 2016-04-20
- Forked [spanishdict/ghost-s3-compat](https://github.com/spanishdict/ghost-s3-compat) from [muzik/ghost-s3](https://github.com/muzix/ghost-s3)

[Unreleased]: https://github.com/spanishdict/ghost-s3-compat/compare/v1.0.2...frankhinek:HEAD
[1.0.2]: https://github.com/spanishdict/ghost-s3-compat/compare/v1.0.1...v1.0.2
[1.0.1]: https://github.com/muzix/ghost-s3/compare/0.2.2...spanishdict:v1.0.1
