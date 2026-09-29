# GCP Linux VM Deployment — `mahesh-linux`

## Overview

This document contains the Google Cloud CLI commands supplied for creating the `mahesh-linux` Ubuntu 24.04 LTS virtual machine.

### VM Details

| Setting | Value |
|---|---|
| VM Name | `mahesh-linux` |
| Project | `project-905207c8-3e76-4ea5-99e` |
| Zone | `us-central1-c` |
| Machine Type | `e2-medium` |
| OS Image | Ubuntu 24.04 LTS |
| Boot Disk | 10 GB |
| Disk Type | `pd-balanced` |
| Network | `default` subnet |
| Network Tier | `PREMIUM` |
| IP Stack | `IPV4_ONLY` |
| Provisioning Model | `STANDARD` |
| Maintenance Policy | `MIGRATE` |
| HTTP/HTTPS Tags | `http-server`, `https-server` |
| Snapshot Retention | 14 days |
| Snapshot Schedule | Daily at `00:00` |

## 1. Create the Linux VM

```bash
gcloud compute instances create mahesh-linux \
    --project=project-905207c8-3e76-4ea5-99e \
    --zone=us-central1-c \
    --machine-type=e2-medium \
    --network-interface=network-tier=PREMIUM,stack-type=IPV4_ONLY,subnet=default \
    --metadata=enable-osconfig=TRUE \
    --maintenance-policy=MIGRATE \
    --provisioning-model=STANDARD \
    --service-account=262761874559-compute@developer.gserviceaccount.com \
    --scopes=https://www.googleapis.com/auth/devstorage.read_only,https://www.googleapis.com/auth/logging.write,https://www.googleapis.com/auth/monitoring.write,https://www.googleapis.com/auth/service.management.readonly,https://www.googleapis.com/auth/servicecontrol,https://www.googleapis.com/auth/trace.append \
    --tags=http-server,https-server \
    --create-disk=auto-delete=yes,boot=yes,device-name=mahesh-inux,image=projects/ubuntu-os-cloud/global/images/ubuntu-2404-noble-amd64-v20260918,mode=rw,size=10,type=pd-balanced \
    --no-shielded-secure-boot \
    --shielded-vtpm \
    --shielded-integrity-monitoring \
    --labels=goog-ops-agent-policy=v2-template-1-7-0,goog-ec-src=vm_add-gcloud \
    --reservation-affinity=any
```

## 2. Create the Google Ops Agent Policy Configuration

Create `config.yaml`:

```bash
printf 'agentsRule:\n  packageState: installed\n  version: latest\ninstanceFilter:\n  inclusionLabels:\n  - labels:\n      goog-ops-agent-policy: v2-template-1-7-0\n' > config.yaml
```

The configuration installs the Google Ops Agent at the latest version for instances matching the label:

```text
goog-ops-agent-policy: v2-template-1-7-0
```

## 3. Create the Ops Agent Policy

```bash
gcloud compute instances ops-agents policies create goog-ops-agent-v2-template-1-7-0-us-central1-c \
    --project=project-905207c8-3e76-4ea5-99e \
    --zone=us-central1-c \
    --file=config.yaml
```

## 4. Create a Daily Snapshot Schedule

The supplied command creates a snapshot schedule with 14-day retention:

```bash
gcloud compute resource-policies create snapshot-schedule default-schedule-1 \
    --project=project-905207c8-3e76-4ea5-99e \
    --region=us-central1 \
    --max-retention-days=14 \
    --on-source-disk-delete=keep-auto-snapshots \
    --daily-schedule \
    --start-time=00:00
```

## 5. Attach the Snapshot Policy to the VM Disk

```bash
gcloud compute disks add-resource-policies mahesh-inux \
    --project=project-905207c8-3e76-4ea5-99e \
    --zone=us-central1-c \
    --resource-policies=projects/project-905207c8-3e76-4ea5-99e/regions/us-central1/resourcePolicies/default-schedule-1
```

## 6. Validation Commands

### Check VM

```bash
gcloud compute instances describe mahesh-linux \
    --project=project-905207c8-3e76-4ea5-99e \
    --zone=us-central1-c
```

### List VMs

```bash
gcloud compute instances list \
    --project=project-905207c8-3e76-4ea5-99e
```

### Check Disk

```bash
gcloud compute disks describe mahesh-inux \
    --project=project-905207c8-3e76-4ea5-99e \
    --zone=us-central1-c
```

### Check Snapshot Policies

```bash
gcloud compute resource-policies list \
    --project=project-905207c8-3e76-4ea5-99e \
    --region=us-central1
```

## 7. Portfolio Learning

This lab demonstrates practical use of:

- Google Cloud Compute Engine
- `gcloud` CLI
- Ubuntu Linux VM provisioning
- Compute Engine machine types
- Network interfaces
- Service accounts and OAuth scopes
- OS Config
- Google Ops Agent policy
- Persistent disks
- Shielded VM configuration
- Automated snapshots
- Resource policies
- Infrastructure automation using CLI

**Repository category:** `Cloud/GCP`

**Suggested location:** `02-GITHUB-PORTFOLIO/Cloud/` or `07-PROJECTS/`

## Important Note

The commands in this document preserve the values from the supplied command. Before reusing them in another environment, review the project ID, service account, zone, image version, disk name, labels, and required permissions.
