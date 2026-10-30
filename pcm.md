# Personal Computing Method

> Organize and manage digital work and tools in a way that separates concerns, controls replication, and supports reproducibility, to maintain control over data and workflows, reduce risk of data loss, and ensure consistent environments across devices.

```mermaid
graph LR
  os[OS]
  subgraph data[User Data]
    subgraph depot[Nonreplicable Data]
      apps[App Components]
      sys[OS Components]
    end
    subgraph docs[Replicable Data]
      subgraph env[Environment Management]
        wam[App Management]
        wpt[OS Management]
      end
      subgraph prv[Private Data]
        bak[Service Backups]
        share[Synced Data]
      end
      pub[Published Data]
      wf[Workflow Data]
      lib[External Data]
    end
  end
  cloud([Cloud])
  removable[[Removable Media]]

  docs -.->|mirror| removable
  pub -.->|upload| cloud
  cloud -.->|download| bak & lib
  env & wf & share <-.->|sync| cloud
  wam --> apps
  wpt --> sys & os

  classDef finalized fill:#d9ead3,stroke:#b6d7a8,color:#333;
  classDef current fill:#c9daf8,stroke:#a4c2f4,color:#333;
  classDef external fill:#d9d2e9,stroke:#b4a7d6,color:#333;
  classDef private fill:#ead1dc,stroke:#d5a6bd,color:#333;
  classDef service fill:#cfe2f3,stroke:#9fc5e8,color:#333;
  classDef device fill:#f4cccc,stroke:#ea9999,color:#333;

  class pub finalized
  class wam,wpt,wf current
  class bak,share private
  class lib external
  class cloud service
  class removable device

  click wam "https://github.com/konskarz/wam"
  click wpt "https://github.com/konskarz/wpt"
```

- **Removable Media**: External storage (e.g., SD-card, phone storage) for local replication to ensure availability offline across devices
- **Cloud**: Cloud Libraries, Services, Storage, Version Control Systems for data consumption, publication and synchronization across devices, use online sync only for actively edited data
- **User Data**: separate OS and user data to reduce risk of data loss
- **Replicable Data**: separate data that should be replicated locally to reduce risk of loss and ensure availability offline across devices
- **Nonreplicable Data**: separate data that doesn’t need replication to optimize storage usage
- **App Components**: portable apps, packages
- **OS Components**: OS images, drivers, updates
- **App Management**: separate app management, used for portability, automation, and workspace integration to enable reproducible workflows across devices, and synchronize it via services to keep it editable across devices
- **OS Management**: separate OS management, used for setup, recovery, and post-install tasks automation, to maintain stable environments, and synchronize it via services to keep configurations consistent across devices
- **Workflow Data**: separate workflow data, synchronized via services to keep it editable across devices
- **Published Data**: separate data intended for publication
- **Private Data**: separate personal data from workflow data to maintain control and privacy
- **Service Backups**: backup personal data from external services to reduce risk of loss
- **Synced Data**: separate personal data synchronized via services to keep it editable across devices
- **External Data**: separate data for consumption, created by others, to avoid mixing with personal workflows and ensure availability offline across devices
