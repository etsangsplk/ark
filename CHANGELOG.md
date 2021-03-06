# Changelog

#### [v0.5.0](https://github.com/heptio/ark/tree/v0.5.0) - 2017-10-26
Breaking changes:
  * The backup tar file format has changed. Backups created using previous versions of Ark cannot be restored using v0.5.0.
  * When backing up one or more specific namespaces, cluster-scoped resources are no longer backed up by default, with the exception of PVs that are used within the target namespace(s). Cluster-scoped resources can still be included by explicitly specifying `--include-cluster-resources`.

New features:
  * Add customized user-agent string for Ark CLI
  * Switch from glog to logrus
  * Exclude nodes from restoration
  * Add a FAQ
  * Record PV availability zone and use it when restoring volumes from snapshots
  * Back up the PV associated with a PVC
  * Add `--include-cluster-resources` flag to `ark backup create`
  * Add `--include-cluster-resources` flag to `ark restore create`
  * Properly support resource restore priorities across cluster-scoped and namespace-scoped resources
  * Support `ark create ...` and `ark get ...`
  * Make ark run as cluster-admin
  * Add pod exec backup hooks
  * Support cross-compilation & upgrade to go 1.9
  
Bug fixes:
  * Make config change detection more robust

#### [v0.4.0](https://github.com/heptio/ark/tree/v0.4.0) - 2017-09-14
Breaking changes:
  * Snapshotting and restoring volumes is now enabled by default
  * The --namespaces flag for 'ark restore create' has been replaced by --include-namespaces and
    --exclude-namespaces

New features:
  * Support for S3 SSE with KMS
  * Cloud provider configurations are validated at startup
  * The persistentVolumeProvider is now optional
  * Restore objects are garbage collected
  * Each backup now has an associated log file, viewable via 'ark backup logs'
  * Each restore now has an associated log file, viewable via 'ark restore logs'
  * Add --include-resources/--exclude-resources for restores

Bug fixes:
  * Only save/use iops for io1 volumes on AWS
  * When restoring, try to retrieve the Backup directly from object storage if it's not found
  * When syncing Backups from object storage to Kubernetes, don't return at the first error
    encountered
  * More closely match how kubectl performs kubeconfig resolution
  * Increase default Azure API request timeout to 2 minutes
  * Update Azure diskURI to match diskName

#### [v0.3.3](https://github.com/heptio/ark/tree/v0.3.3) - 2017-08-10
  * Treat the first field in a schedule's cron expression as minutes, not seconds

#### [v0.3.2](https://github.com/heptio/ark/tree/v0.3.2) - 2017-08-07
  * Add client-go auth provider plugins for Azure, GCP, OIDC

#### [v0.3.1](https://github.com/heptio/ark/tree/v0.3.1) - 2017-08-03
  * Fix Makefile VERSION

#### [v0.3.0](https://github.com/heptio/ark/tree/v0.3.0) - 2017-08-03
  * Initial Release
