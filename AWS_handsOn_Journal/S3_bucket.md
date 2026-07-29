# S3 — Create, Upload, and Delete a Bucket

## What I did
- Created a private S3 bucket using the new **Account Regional namespace** option (bucket name only needs to be unique within my own account, not globally)
- Left all default security settings in place: ACLs disabled, Block Public Access fully enabled, versioning disabled, default SSE-S3 encryption
- Uploaded a test file into the bucket
- Tried opening the file two ways:
  - Direct object URL, copy-pasted into browser → **Access Denied**
  - "Open" button inside the S3 console (while logged in as my IAM user) → worked fine
- Deleted the object, then deleted the bucket itself, with confirmation typing required for both

## What I learned
- **Block Public Access** means even a direct object URL fails without proper authentication — the file being "in my account" doesn't mean it's reachable by just anyone with the link.
- The console's "Open" button works because AWS generates a **temporary, signed, authenticated request** using my logged-in IAM credentials — not because the object is public. This is the actual mechanism behind private-by-default access.
- AWS now offers an **Account Regional namespace** for bucket names (in addition to the traditional global namespace) — this avoids the classic "bucket name already taken" problem, since the name only has to be unique within my own account + region.
- Deleting objects and buckets both require typing a confirmation phrase/name — deliberate friction against accidental deletion.
- Used my IAM user (not root) for this entire exercise, as intended — root is reserved for account-level tasks only.


![alt text](<Screenshot 2026-07-28 183916.png>)

![](<Screenshot 2026-07-28 183900.png>)

