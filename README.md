# Terraform_ya_lab
Deploy-VM-To-YandexCloud-byTerraform

## How it works: 

1. Clone repo to your PC: 
```
git clone git@github.com:molchanovar/Terraform_ya_lab.git
```

2. Input your own values in terraform.tfvars: 
```
mv terraform.tfvars.example terraform.tfvars
```

3. Run cloud infrastructure by terraform:

``` 
terraform init
terraform plan
terraform apply
```

4. Terraform output: 
<details>
  <summary markdown="span">terraform plan</summary>

```
Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the following symbols:
  + create

Terraform will perform the following actions:

  # yandex_compute_instance.vm-1 will be created
  + resource "yandex_compute_instance" "vm-1" {
      + created_at                = (known after apply)
      + folder_id                 = (known after apply)
      + fqdn                      = (known after apply)
      + hostname                  = (known after apply)
      + id                        = (known after apply)
      + metadata                  = {
          + "ssh-keys" = <<-EOT
                ubuntu:ssh-rsa *****
            EOT
        }
      + name                      = "terraform1"
      + network_acceleration_type = "standard"
      + platform_id               = "standard-v1"
      + service_account_id        = (known after apply)
      + status                    = (known after apply)
      + zone                      = (known after apply)

      + boot_disk {
          + auto_delete = true
          + device_name = (known after apply)
          + disk_id     = (known after apply)
          + mode        = (known after apply)

          + initialize_params {
              + description = (known after apply)
              + image_id    = "fd83klic6c8gfgi40urb"
              + name        = (known after apply)
              + size        = (known after apply)
              + snapshot_id = (known after apply)
              + type        = "network-hdd"
            }
        }

      + network_interface {
          + index              = (known after apply)
          + ip_address         = (known after apply)
          + ipv4               = true
          + ipv6               = (known after apply)
          + ipv6_address       = (known after apply)
          + mac_address        = (known after apply)
          + nat                = true
          + nat_ip_address     = (known after apply)
          + nat_ip_version     = (known after apply)
          + security_group_ids = (known after apply)
          + subnet_id          = (known after apply)
        }

      + placement_policy {
          + placement_group_id = (known after apply)
        }

      + resources {
          + core_fraction = 20
          + cores         = 2
          + memory        = 2
        }

      + scheduling_policy {
          + preemptible = true
        }
    }

  # yandex_vpc_network.network-1 will be created
  + resource "yandex_vpc_network" "network-1" {
      + created_at                = (known after apply)
      + default_security_group_id = (known after apply)
      + folder_id                 = (known after apply)
      + id                        = (known after apply)
      + labels                    = (known after apply)
      + name                      = "network1"
      + subnet_ids                = (known after apply)
    }

  # yandex_vpc_subnet.subnet-1 will be created
  + resource "yandex_vpc_subnet" "subnet-1" {
      + created_at     = (known after apply)
      + folder_id      = (known after apply)
      + id             = (known after apply)
      + labels         = (known after apply)
      + name           = "subnet1"
      + network_id     = (known after apply)
      + v4_cidr_blocks = [
          + "192.168.10.0/24",
        ]
      + v6_cidr_blocks = (known after apply)
      + zone           = "ru-central1-a"
    }

Plan: 3 to add, 0 to change, 0 to destroy.

Changes to Outputs:
  + external_ip_address_vm_1 = (known after apply)
  + internal_ip_address_vm_1 = (known after apply)

Do you want to perform these actions?
  Terraform will perform the actions described above.
  Only 'yes' will be accepted to approve.

  Enter a value: yes
  
```  
</details>

<details>
  <summary markdown="span">Creating output</summary>

```
yandex_compute_instance.vm-1 (remote-exec): Connecting to remote host via SSH...
yandex_compute_instance.vm-1 (remote-exec):   Host: 178.154.220.228
yandex_compute_instance.vm-1 (remote-exec):   User: ubuntu
yandex_compute_instance.vm-1 (remote-exec):   Password: false
yandex_compute_instance.vm-1 (remote-exec):   Private key: true
yandex_compute_instance.vm-1 (remote-exec):   Certificate: false
yandex_compute_instance.vm-1 (remote-exec):   SSH Agent: true
yandex_compute_instance.vm-1 (remote-exec):   Checking Host Key: false
yandex_compute_instance.vm-1 (remote-exec):   Target Platform: unix
yandex_compute_instance.vm-1 (remote-exec): Connected!
yandex_compute_instance.vm-1 (remote-exec): Im ready!
yandex_compute_instance.vm-1: Provisioning with 'local-exec'...

yandex_compute_instance.vm-1 (local-exec): changed: [178.154.220.228]

yandex_compute_instance.vm-1 (local-exec): TASK [Install nginx] ***********************************************************
yandex_compute_instance.vm-1: Still creating... [5m51s elapsed]
yandex_compute_instance.vm-1: Still creating... [6m1s elapsed]
yandex_compute_instance.vm-1 (local-exec): changed: [178.154.220.228]

yandex_compute_instance.vm-1 (local-exec): TASK [Enable nginx] ************************************************************
yandex_compute_instance.vm-1 (local-exec): changed: [178.154.220.228]

yandex_compute_instance.vm-1 (local-exec): PLAY RECAP *********************************************************************
yandex_compute_instance.vm-1 (local-exec): 178.154.220.228            : ok=4    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

yandex_compute_instance.vm-1: Creation complete after 6m3s [id=fhme5lqejim5uj0en342]

Apply complete! Resources: 3 added, 0 changed, 0 destroyed.

Outputs:

external_ip_address_vm_1 = "178.154.220.228"
internal_ip_address_vm_1 = "192.168.10.11"
```
</details>


### Useful links: 
1. [**YandexProvider**](https://registry.terraform.io/providers/yandex-cloud/yandex/latest)
2. [**TerraformProvisioners**](https://www.terraform.io/docs/language/resources/provisioners/syntax.html)
3. [**AnsibleNginx**](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)
