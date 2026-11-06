# WORKING WITH EBS
## NAME: BHARATH S
## REG NO: 212225230031

## Aim

To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

---

## Algorithm / Steps

1. Create a new Amazon EBS volume with a size of 1 GiB.
2. Select the same Availability Zone as the EC2 instance.
3. Attach the EBS volume to the EC2 instance using `/dev/sdb`.
4. Connect to the EC2 instance using AWS Systems Manager Session Manager.
5. Check the available storage using `df -h`.
6. Create an `ext3` file system on the EBS volume.
7. Create the `/mnt/data-store` directory.
8. Mount the EBS volume to `/mnt/data-store`.
9. Configure `/etc/fstab` for automatic mounting.
10. Verify that the EBS volume is successfully mounted.
11. Create `file.txt` inside the mounted EBS volume.
12. Verify the contents of the created file.
13. Create an EBS snapshot named `My Snapshot`.
14. Delete `file.txt` from the original EBS volume.
15. Create a new EBS volume from the snapshot.
16. Attach the restored volume to the EC2 instance using `/dev/sdc`.
17. Create the `/mnt/data-store2` directory.
18. Mount the restored volume to `/mnt/data-store2`.
19. Verify that `file.txt` has been successfully restored.

---

## Program

### 1. Check Available Storage

```bash
df -h
```

### 2. Create an ext3 File System

```bash
sudo mkfs -t ext3 /dev/sdb
```

### 3. Create a Mount Directory

```bash
sudo mkdir /mnt/data-store
```

### 4. Mount the EBS Volume

```bash
sudo mount /dev/sdb /mnt/data-store
```

### 5. Configure Automatic Mounting

```bash
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```

### 6. View the File System Configuration

```bash
cat /etc/fstab
```

### 7. Verify the Mounted Volume

```bash
df -h
```

### 8. Create a File in the EBS Volume

```bash
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```

### 9. Read the File

```bash
cat /mnt/data-store/file.txt
```

### 10. Delete the File

```bash
sudo rm /mnt/data-store/file.txt
```

### 11. Verify File Deletion

```bash
ls /mnt/data-store/
```

### 12. Create a Mount Directory for the Restored Volume

```bash
sudo mkdir /mnt/data-store2
```

### 13. Mount the Restored EBS Volume

```bash
sudo mount /dev/sdc /mnt/data-store2
```

### 14. Verify Snapshot Restoration

```bash
ls /mnt/data-store2/
```

Expected output:

```text
file.txt
```

---

## Outputs
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085600" src="https://github.com/user-attachments/assets/8478b3eb-7200-42c3-83c0-ad8e3dab2760" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085521" src="https://github.com/user-attachments/assets/df38060e-1c6c-48d8-860a-d4dc6b5a63df" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085416" src="https://github.com/user-attachments/assets/8ebf3693-e83d-448f-9e76-f99bc6010efa" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085300" src="https://github.com/user-attachments/assets/a711f4eb-ae2d-475f-97a7-3dc8d69dba45" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085129" src="https://github.com/user-attachments/assets/fa24baab-b87f-494a-884b-03bd00690da8" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085022" src="https://github.com/user-attachments/assets/53d30f7c-f9b1-4c4e-b975-a5fe64ec9504" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 084827" src="https://github.com/user-attachments/assets/4db0f19a-44b2-48f8-9ce2-c266dae53e2d" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 084454" src="https://github.com/user-attachments/assets/4268d80d-b85a-4613-bfe3-3bbc254437b8" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 084323" src="https://github.com/user-attachments/assets/df3d6705-ef28-4599-b398-6b566ad96035" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 084310" src="https://github.com/user-attachments/assets/61abdc39-2301-4a5b-bcac-11d42bfcf369" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 084116" src="https://github.com/user-attachments/assets/8560b2b5-ccce-4da1-84a3-c468b20e7009" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 084002" src="https://github.com/user-attachments/assets/6b47ada7-ae8f-4846-955a-453c0a9eb18d" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 083606" src="https://github.com/user-attachments/assets/72082766-0f8f-4886-af20-f12fdc46c361" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 083413" src="https://github.com/user-attachments/assets/2e32ca79-4935-45e0-898d-4d406dcd6f0f" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 083350" src="https://github.com/user-attachments/assets/353bcec2-c73c-4311-9cab-69cd0997e49e" />
<img width="638" height="461" alt="Screenshot 2026-11-05 082136" src="https://github.com/user-attachments/assets/d4fe0602-8400-47df-bdf6-248d2e455672" />
<img width="1920" height="1080" alt="Screenshot 2026-11-03 202615" src="https://github.com/user-attachments/assets/8d72d391-c1ec-4848-96a5-92a378d257f6" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085848" src="https://github.com/user-attachments/assets/9b172b83-0c3e-478b-8128-27640871a4e8" />
<img width="1920" height="1080" alt="Screenshot 2026-11-06 085643" src="https://github.com/user-attachments/assets/33f2d8b7-78b6-4679-8670-835a46690ac0" />







## Result
Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.

