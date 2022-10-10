# bitcompat project

This project aims to provide 100% open-source drop-in replacement
images for bitnami-packaged docker images.

The provided images are handwritten and curated, with the same features,
pre-installed software and directory structure, and they are comparable
in size (same size of the bitnami ones or smaller).

## Why?

The main reason is to provide multi-arch compatible images based on minideb.

After ARM64 compatibility has been merged in minideb, it was expected that
the most used software will be repackaged to support ARM64 arch too.  
2 years have been passed, but no ETA or plan to fully support architectures
other than x86-64 is present.

Additionally, the real sources of the packages is hidden because the
pre-packaged software is downloaded from the bitnami servers.

On the contrary, this project will be 100% open-source, clearly describing how the 
software is built and packaged, giving anyone the chance to contribute.

## How?

The original bitnami images are the real source of truth. The startup
scripts are simply copied (where the license allows to do so) and the
remaining parts are reverse-engineered, comparing for example, the
directory structure.

The packages are mainly compiled from source while their dependencies are
often installed via apt and the debian repositories.

Once built, the tree of the image's filesystem is manually compared to the
original one and the eventual differences are corrected.

However, small differences could be unavoidable, but they are kept to the
very minimum.

The env variables are also manually compared, to have exactly the same
env vars set while building a new image on top of these images.

As the final stage, images' sizes are compared to the original ones:
if they are roughly the same (~ 10mb) or smaller, the image is ok to
be released.

## What?

As this is a very young project, only a few images have been published

- [Java](https://github.com/bitcompat/java) (11, 17, 18, 19)
- [Kafka](https://github.com/bitcompat/kafka) (3.1, 3.2, 3.3)
- [Nginx](https://github.com/bitcompat/nginx) (1.22, 1.23)
- [Nginx Prometheus Exporter](https://github.com/bitcompat/nginx-exporter) (0.11)
- [PHP-FPM](https://github.com/bitcompat/php-fpm) (7.4, 8.0, 8.1)
- [Postgres Prometheus Exporter](https://github.com/bitcompat/postgres-exporter) (0.11)
- [PostgreSQL](https://github.com/bitcompat/postgresql) (10, 11, 12, 13, 14)
- [Redis](https://github.com/bitcompat/redis) (6, 7)
- [Zookeeper](https://github.com/bitcompat/zookeeper) (3.8, 3.7, 3.6)

but many others are planned!

## Where?

All the images are published on GitHub Registry and on AWS Public ECR Gallery.  
Further information are present on the images' README files.

## Contributions

Contributions are always welcome!

Found a difference from the original image? Feel free to open an issue
in the image repository or submit a PR with the correction: it will be
reviewed as soon as possibile!

For the feature requests and the new images, please use the "containers"
repository. New images will be manually reviewed and, when accepted, a
new repository will be created.

## Can I use it in production?

Production-grade quality is required for all images, but we cannot
guarantee the images are free of bugs or defects.

We don't take any responsibility for any loss or damage the use of
these images could cause.  
USE THEM AT YOUR OWN RISK

## License

All the code published here is licensed under MIT license.  

## Notes

Bitnami is a registered trademark of VMware, Inc.  
This project is NOT related to or endorsed by Bitnami or its affiliates.

The packaged software retain their own licenses, which are present
inside the package itself.
