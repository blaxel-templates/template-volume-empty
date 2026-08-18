# Blaxel Volume template

<p align="center">
  <img src="https://blaxel.ai/logo.png" alt="Blaxel" width="200"/>
</p>

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Blaxel](https://img.shields.io/badge/Blaxel-Volume-brightgreen.svg)](https://blaxel.ai/)

</div>

A volume template for the Blaxel platform that allows you to create reusable storage templates with prepopulated files and directories. Deploy this as a volume template, then create volumes from it that will automatically contain all your pre-configured files, perfect for sharing data, configurations, or resources across your agents and jobs.

## 📑 Table of Contents

- [Blaxel Volume template](#blaxel-volume-template)
  - [📑 Table of Contents](#-table-of-contents)
  - [✨ Features](#-features)
  - [🚀 Quick Start](#-quick-start)
  - [📋 Prerequisites](#-prerequisites)
  - [💻 Installation](#-installation)
  - [🔧 Usage](#-usage)
    - [Adding Files to Your Volume Template](#adding-files-to-your-volume-template)
    - [Deploying the Volume Template](#deploying-the-volume-template)
    - [Creating Volumes from the Template](#creating-volumes-from-the-template)
  - [📁 Project Structure](#-project-structure)
  - [❓ Troubleshooting](#-troubleshooting)
    - [Common Issues](#common-issues)
  - [👥 Contributing](#-contributing)
  - [🆘 Support](#-support)
  - [📄 License](#-license)

## ✨ Features

- Reusable volume templates with prepopulated files and directories
- Create multiple volumes from a single template
- Easy file management and organization
- Seamless integration with Blaxel platform for cloud deployment
- Share data and configurations across multiple agents and jobs
- Version-controlled volume templates
- Simple two-step workflow: deploy template, create volumes
- Flexible volume mounting and access

## 🚀 Quick Start

For those who want to get up and running quickly:

```bash
# Create a volume template from this repository
bl new volumetemplate YOUR-TEMPLATE-NAME

# Navigate to the project directory
cd YOUR-TEMPLATE-NAME

# Add your files to the template directory
# (files you want to be prepopulated in volumes created from this template)

# Deploy the volume template to Blaxel
bl deploy

# Wait for your volume template to be deployed
bl get volumetemplate YOUR-TEMPLATE-NAME --watch
```

## 📋 Prerequisites

- **Blaxel Platform Setup:** Complete Blaxel setup by following the [quickstart guide](https://docs.blaxel.ai/Get-started#quickstart)
  - **[Blaxel CLI](https://docs.blaxel.ai/Get-started):** Ensure you have the Blaxel CLI installed. If not, install it globally:
    ```bash
    curl -fsSL https://raw.githubusercontent.com/blaxel-ai/toolkit/main/install.sh | BINDIR=/usr/local/bin sudo -E sh
    ```
  - **Blaxel login:** Login to Blaxel platform
    ```bash
    bl login YOUR-WORKSPACE
    ```

## 💻 Installation

**Clone the repository:**

```bash
git clone https://github.com/blaxel-ai/template-volume-empty.git
cd template-volume-empty
```

No additional dependencies need to be installed. Simply add your files to the directory and deploy.

## 🔧 Usage

### Adding Files to Your Volume Template

Add any files or directories you want to be prepopulated in volumes created from this template:

```bash
# Create directories
mkdir -p data/configs

# Add your files
cp /path/to/your/files/* data/
echo "Sample configuration" > data/configs/config.yaml

# Add any data, scripts, or resources you need
```

All files and directories in your template directory will be included in volumes created from it.

### Deploying the Volume Template

When you are ready to deploy your volume template to the cloud:

```bash
bl deploy
```

This command uses your files and the configuration in `blaxel.toml` to deploy your volume template on the Blaxel platform.

### Creating Volumes from the Template

Once your template is deployed, you can create volumes from it:

```typescript
import { VolumeInstance } from "@blaxel/core";

const volume = await VolumeInstance.create({
  name: "test-persistence-volume",
  template: "YOUR-TEMPLATEE-NAME",
});
```

You can create multiple volumes from the same template. Each volume will contain a copy of all the template's files. These volumes can then be attached to agents or jobs by referencing them in their configuration.

## 📁 Project Structure

- **blaxel.toml** - Blaxel deployment configuration (volumetemplate type)
- **Your files and directories** - Add any files you want prepopulated in volumes created from this template

## ❓ Troubleshooting

### Common Issues

1. **Template Deployment Issues**:
   - Ensure you're logged in to your workspace: `bl login MY-WORKSPACE`
   - Verify volume template deployment: `bl get volumetemplates`
   - Check that your `blaxel.toml` is properly configured for volumetemplate type

2. **File Issues**:
   - Ensure files you want to prepopulate are in the template directory before deploying
   - Check file permissions if having access issues
   - Verify file sizes are within reasonable limits

3. **Volume Creation Issues**:
   - Verify the volume template is deployed: `bl get volumetemplates`
   - Ensure you're referencing the correct template name when creating volumes
   - Check volume creation status: `bl get volumes`

4. **Volume Access Issues**:
   - Verify the volume exists: `bl get volumes`
   - Ensure agents/jobs are properly configured to mount the volume
   - Ensure your Blaxel CLI is up to date

For more help, please [submit an issue](https://github.com/blaxel-templates/template-volume-empty/issues) on GitHub.

## 👥 Contributing

Contributions are welcome! Here's how you can contribute:

1. **Fork** the repository
2. **Create** a feature branch:
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit** your changes:
   ```bash
   git commit -m 'Add amazing feature'
   ```
4. **Push** to the branch:
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Submit** a Pull Request

Please make sure to test your changes with Blaxel deployment.

## 🆘 Support

If you need help with this template:

- [Submit an issue](https://github.com/blaxel-templates/template-volume-empty/issues) for bug reports or feature requests
- Visit the [Blaxel Documentation](https://docs.blaxel.ai) for platform guidance
- Check the [Blaxel Volume Template Documentation](https://docs.blaxel.ai/volumetemplate) for volume template-specific help
- Join our [Discord Community](https://discord.gg/CsWKUZUHFQ) for real-time assistance

## 📄 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.