# Ghost S3 Custom Storage Module

This module allows you to read and write images from Amazon S3 instead of
storing them locally.

After installing, new images that you save will use an absolute URL to S3. Any
requests to `/content/images/` will be proxied to S3, so that any previous
images in your blog will not be affected.

## Installation

You will need to have a the custom storage module directly in your project
directory, the easiest way to do this is to change to the directory your ghost
installation and execute the following commands:

```bash
$ npm install ghost-storage-s3
$ npm shrinkwrap
```

## Create Storage Module

Create a directory to store your custom storage module:

```bash
$ sudo mkdir -p content/storage/ghost-s3
```

In the `ghost-s3/` directory you need to create a file named `index.js` with the following
contents:

```javascript
'use strict';
module.exports = require('ghost-storage-s3');
```

## Configuration

Create new IAM User with permissions to get object from that bucket. Save the `ACCESS_KEY` and `SECRET_ACCESS_KEY`.

In `config.js`, add a `storage` block for each environment. A list of valid regions can be accessed in the AWS General Reference of [S3 AWS Regions and Endpoints](http://docs.aws.amazon.com/general/latest/gr/rande.html#s3_region).

```javascript
    storage: {
        active: 'ghost-s3',
        'ghost-s3': {
            accessKeyId: 'ACCESS_KEY',
            secretAccessKey: 'SECRET_ACCESS_KEY',
            bucket: 'S3_BUCKET_NAME',
            region: 'S3_REGION'
        }
    }
```

## Asset Host

You can add `assetHost` to your config to specify a virtual host url. This is most frequently used with a content delivery network (CDN) such as CloudFront, CloudFlare, or others.  The modified `storage` block would be:

```javascript
    storage: {
        active: 'ghost-s3',
        'ghost-s3': {
            accessKeyId: 'ACCESS_KEY',
            secretAccessKey: 'SECRET_ACCESS_KEY',
            bucket: 'S3_BUCKET_NAME',
            region: 'S3_REGION',
            assetHost: 'https://cdn.yourdomain.com/'
        }
    }
```

For more information, read the [Virtual Hosting of Buckets](http://docs.aws.amazon.com/AmazonS3/latest/dev/VirtualHosting.html)
section of the AWS S3 Developer Guide.

## Copyright & License

- Original work Copyright (c) 2015 Hoang Pham Huu <phamhuuhoang@gmail.com>
- Modified work Copyright (c) 2016 Curiosity Media, Inc.
- Modified work by Frank Hinek

Released under the [MIT license](https://github.com/muzix/ghost-s3/blob/master/LICENSE).
