---
title: "Should you include .terraform.lock.hcl in .gitignore?"
datePublished: Sun Feb 11 2024 16:34:14 GMT+0000 (Coordinated Universal Time)
cuid: clshq6lq4000109ju61pebt3e
slug: terraform-lock-hcl-to-gitignore-or-commit
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707666218132/d66439c0-b5c6-48b0-b954-fae90f887e3f.png
tags: version-control, git, terraform

---

One question that I had in my mind when I first build my IaC(Infrastructure as Code) with Terraform was, what all needs to be included in the `.gitignore`, especially the `.terraform.lock.hcl`.

![.terraform.lock.hcl file in VSCode, ready to be committed to repository](https://cdn.hashnode.com/res/hashnode/image/upload/v1707665594211/3eae31bb-cace-49ff-b2ab-b70cf6c3eb55.png align="center")

So here is the quick answer: **Yes, you should commit** the `.terraform.lock.hcl` to your version control (GitHub repository).

Let's first see, what is the `.terraform.lock.hcl`. According to [Hashicorp's documentation](https://developer.hashicorp.com/terraform/language/files/dependency-lock)

> Terraform automatically creates or updates the dependency lock file each time you run [the `terraform init` command. You should include this](https://developer.hashicorp.com/terraform/cli/commands/init) file in your version control repository so that you can discuss potential changes to your external dependencies via code review, just as you would discuss potential changes to your configuration itself.

When `terraform init` is working on installing all of the providers needed for a configuration, Terraform considers both the version constraints in the configuration *and* the version selections recorded in the lock file.

If a particular provider has no existing recorded selection, Terraform will select the newest available version that matches the given version constraint, and then update the lock file to include that selection.

If a particular provider already has a selection recorded in the lock file, Terraform will always re-select that version for installation, even if a newer version has become available. You can override that behaviour by adding the `-upgrade` option when you run `terraform init`, in which case Terraform will disregard the existing selections and once again select the newest available version matching the version constraint.

Basically, `.terraform.lock.hcl` allows Terraform to keep on utilizing the version of the provider selected when you added it. In the event that you don't checkin the lock file, you will automatically be upgraded to the latest version, which may lead to broken changes.

## Support multiple platforms

You may have developers who work with your Terraform code on different OS machines: Windows, macOS or Linux.  
This is where you could choose to verify that all of your providers support all of those platforms, and to pre-populate the lock file with the necessary checksums, you can do so by running `terraform providers lock` and specifying those three platforms:

```bash
terraform providers lock \
  -platform=windows_amd64 \ # 64-bit Windows
  -platform=darwin_amd64 \  # 64-bit macOS
  -platform=linux_amd64     # 64-bit Linux
```

![running the terraform providers lock command to support multiple systems](https://cdn.hashnode.com/res/hashnode/image/upload/v1707665446997/6a88bb21-c193-44a1-a162-0b1937371c69.png align="center")

After the command has run successfully, you will also see that output mentions:

> Review the changes in .terraform.lock.hcl and then commit to your version control system to retain the new checksums.

![Output after the terraform provider lock command is run successfully.](https://cdn.hashnode.com/res/hashnode/image/upload/v1707665483448/f45f3494-eabf-40e6-b6a9-f6985293ed55.png align="center")

You can read more about the `provider lock` command [here.](https://www.terraform.io/cli/commands/providers/lock)

## Terraform `.gitignore` file

And just for the reference, here is the Terraform `.gitignore` file.

```yaml
# Local .terraform directories
**/.terraform/*

# .tfstate files
*.tfstate
*.tfstate.*

# Crash log files
crash.log
crash.*.log

# Exclude all .tfvars files, which are likely to contain sensitive data, such as
# password, private keys, and other secrets. These should not be part of version 
# control as they are data points which are potentially sensitive and subject 
# to change depending on the environment.
*.tfvars
*.tfvars.json

# Ignore override files as they are usually used to override resources locally and so
# are not checked in
override.tf
override.tf.json
*_override.tf
*_override.tf.json

# Include override files you do wish to add to version control using negated pattern
# !example_override.tf

# Include tfplan files to ignore the plan output of command: terraform plan -out=tfplan
# example: *tfplan*

# Ignore CLI configuration files
.terraformrc
terraform.rc
```

Hope you found this article helpful. I am Rishab, who loves writing and sharing content around cloud computing and DevOps. I also have a YouTube channel - [Rishab in Cloud.](https://youtube.com/@rishabincloud)