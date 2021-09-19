# Vault Server on Synology

1. click Vault image (launch `Create Container` window)

   ![Create Container](./images/Vault_on_Synology_01.png "Create Container")

1. Enable auto-restart

   ![Enable auto-restart](./images/Vault_on_Synology_02.png "Enable auto-restart")

1. Add folders

   - docker/vault/config : /vault/config
   - docker/vault/file : /vault/file
   - docker/vault/logs : /vault/logs

   ![Add volumes](./images/Vault_on_Synology_03.png "Add volumes")

1. `Netwotk` tab (no change)

   ![Network settings](./images/Vault_on_Synology_04.png "Network settings")

1. Port forwarding `8200:8200`

   ![-p 8200:8200](./images/Vault_on_Synology_05.png "-p 8200:8200")

1. `Links` tab (no change)

   ![Links settings](./images/Vault_on_Synology_06.png "Links settings")

1. Command:

   - `vault server -config\=/vault/config/vault.hcl`

   ![Entrypoint](./images/Vault_on_Synology_07.png "Entrypoint")

1. Done!

   ![Done!](./images/Vault_on_Synology_08.png "Done!")

---

- Vault configuration (`vault.hcl`)

  ```conf:/vault/config/vault.hcl
  disable_mlock = true
  ui            = true

  storage "file" {
    path = "/vault/data"
  }

  listener "tcp" {
    address         = "0.0.0.0:8200"
    tls_disable     = 1
  }
  ```
