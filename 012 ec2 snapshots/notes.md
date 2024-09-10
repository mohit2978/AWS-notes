# EC2 continued
## Snapshots

### EBS snapshots
EBS snapshots are the backups of the EBS volumes at a particular instant. Snapshots are typically stored in an S3 bucket, only accessible through the S3 API or AWS CLI. They contain the entire information required to restore the data in an EBS volume.

EBS snapshots are incremental. This means we only take snapshots of the data added after the most recent snapshot to save time and storage space. Therefore, the first snapshot is a full snapshot of all the blocks in the volume. The next snapshot would be an incremental snapshot of only the blocks added or modified after the last snapshot.

EBS snapshots provide multiple features to lock a snapshot and protect it from malicious activities and deletion, monitor the snapshot locks, and copy a snapshot. In short, EBS ensures that our data is recoverable and safe.

EBS snapshots are regionally resilient. The duplicates of snapshots are stored across multiple AZs in a region, so if one AZ fails, another takes over. We can use snapshots to restore the data in other AZs and to migrate the data.

### Fast Snapshot Restore (FSR)
EBS volumes lazily restore volumes from an S3 bucket. If we try to access any block of data that has not been loaded yet, EBS fetches it from S3 urgently. However, this is not as quick as reading directly from the EBS volumes.

EBS snapshots offer Fast Snapshot Restore (FSR) to resolve this issue. It instantly restores a fully initiated EBS volume from the snapshot, eliminating the I/O latency when it is first accessed.

To leverage FSR, we must explicitly enable FSR for the snapshot and specify an availability zone. Upon restoration from that snapshot, a fully initiated EBS volume is restored in the specified availability zone.

### EBS encryption
Amazon Elastic Block Store encryption is a feature that allows us to encrypt our EBS volumes and snapshots using industry-standard AES-256 data encryption. It uses AWS Key Management Service (KMS), a service that allows us to create and control encryption keys. Encryption occurs on the host EC2 servers, which protect data at rest and in transit. The following data is encrypted in EBS encryption:

- Data at rest inside the volume

- Data in transit between the volume and the instance

- Snapshots created from the volume

- Volumes created using encrypted snapshot