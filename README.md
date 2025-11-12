# PowerApp-Form

A Microsoft Power Apps canvas application featuring a generic form template with name, email, and message input fields. This project is structured for version control and easy import into the Power Platform.

## 🎯 Overview

This is a ready-to-use Power Apps form template that demonstrates best practices for building canvas apps. The form includes basic input validation, responsive design, and a clean user interface suitable for data collection scenarios.

## ✨ Features

- **Responsive Form Layout**: Adapts to different screen sizes
- **Multiple Input Types**: 
  - Single-line text input (Name, Email)
  - Multi-line text area (Message)
- **Submit Functionality**: Button with success notification
- **Professional Design**: Clean blue header with white form fields
- **Mobile-Friendly**: Optimized for portrait orientation (720x1280)
- **Version Control Ready**: Human-readable JSON/YAML format

## 📁 Project Structure

```
PowerApp-Form/
├── CanvasManifest.json          # Main app manifest
├── Properties.json               # App properties
├── Header.json                   # Version information
├── .gitignore                    # Git ignore rules
├── README.md                     # This file
├── POWERAPP_STRUCTURE.md         # Detailed structure docs
│
├── References/                   # App references
│   ├── DataSources.json         # Data source references
│   ├── Resources.json           # Resource references
│   └── Themes.json              # Theme configuration
│
└── Src/                         # Source code (Power Fx)
    ├── Screen1.fx.yaml          # Main screen definition
    └── EditorState/             # Editor state files
        └── Screen1.editorstate.json
```

## 🚀 Quick Start

### Option 1: Import into Power Apps

1. **Package the app**:
   ```bash
   cd PowerApp-Form
   zip -r PowerApp-Form.msapp *
   ```

2. **Import to Power Platform**:
   - Navigate to [make.powerapps.com](https://make.powerapps.com)
   - Click **Apps** → **Import canvas app**
   - Upload `PowerApp-Form.msapp`
   - Configure environment settings
   - Click **Import**

### Option 2: Edit Locally

1. **Clone the repository**:
   ```bash
   git clone https://github.com/mcdugal19/PowerApp-Form.git
   cd PowerApp-Form
   ```

2. **Open in Power Apps Studio**:
   - Launch Power Apps Studio
   - Click **Open** → **Browse**
   - Select the PowerApp-Form folder
   - Start editing

## 📝 Form Fields

The default form includes:

| Field | Type | Properties |
|-------|------|------------|
| **Header** | Label | Blue background, white text |
| **Name** | Text Input | Single-line, required |
| **Email** | Text Input | Single-line, email format |
| **Message** | Text Input | Multi-line, larger text area |
| **Submit** | Button | Triggers success notification |
| **Status** | Label | Displays form status messages |

## 🎨 Customization

### Change Form Title

Edit `Src/Screen1.fx.yaml`:
```yaml
HeaderLabel As label:
    Text: ="Your Custom Title"
```

### Add New Input Field

Add to `Src/Screen1.fx.yaml`:
```yaml
PhoneLabel As label:
    Text: ="Phone:"
    Y: =500
    
PhoneInput As text:
    HintText: ="Enter phone number"
    Y: =540
```

### Connect to Data Source

Modify the submit button's `OnSelect` property:
```yaml
OnSelect: |
    =Patch(
        YourDataSource,
        Defaults(YourDataSource),
        {
            Name: NameInput.Text,
            Email: EmailInput.Text,
            Message: MessageInput.Text
        }
    );
    Notify("Form submitted successfully!", NotificationType.Success)
```

## 🔧 Development Workflow

### Making Changes

1. Edit `.fx.yaml` files in the `Src/` directory
2. Test changes in Power Apps Studio
3. Commit changes to version control

### Adding Data Connections

1. Open app in Power Apps Studio
2. Add data source (SharePoint, SQL, Dataverse, etc.)
3. Connection details saved in `References/DataSources.json`
4. Update `.gitignore` to exclude sensitive connection strings

### Team Collaboration

This structure enables effective team collaboration:
- ✅ Changes are trackable in Git
- ✅ Files are human-readable (JSON/YAML)
- ✅ Code reviews are possible
- ✅ Merge conflicts are manageable

## 📚 Documentation

For detailed information about the project structure and customization options, see:
- [POWERAPP_STRUCTURE.md](POWERAPP_STRUCTURE.md) - Complete structure documentation

## 🛠️ Tech Stack

- **Platform**: Microsoft Power Platform
- **Language**: Power Fx (Formula Language)
- **Format**: Canvas App (.msapp)
- **File Structure**: JSON/YAML

## 📖 Resources

- [Power Apps Documentation](https://docs.microsoft.com/powerapps/)
- [Power Fx Documentation](https://docs.microsoft.com/power-platform/power-fx/)
- [Canvas App Formula Reference](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [Power Apps Community](https://powerusers.microsoft.com/t5/Power-Apps-Community/ct-p/PowerApps1)

## 🔐 Security Notes

- Connection strings and secrets are excluded via `.gitignore`
- Do not commit sensitive data source credentials
- Review data permissions in Power Platform admin center
- Follow your organization's security policies

## 📦 Version Information

- **App Version**: 2024-11-12T20:25:00.000Z
- **Doc Version**: 1.333
- **Min Version to Load**: 1.331
- **Structure Version**: 2.0

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Make your changes
4. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
5. Push to the branch (`git push origin feature/AmazingFeature`)
6. Open a Pull Request

## 📄 License

This project is provided as-is for educational and development purposes.

## 👤 Author

**Lance McDaniel**
- GitHub: [@mcdugal19](https://github.com/mcdugal19)

## 🌟 Next Steps

- [ ] Add form validation
- [ ] Connect to a data source (SharePoint/Dataverse)
- [ ] Add more screens for multi-step forms
- [ ] Implement user authentication
- [ ] Add custom themes and branding
- [ ] Create automated testing

---

**Need Help?** Check out the [Power Apps Documentation](https://docs.microsoft.com/powerapps/) or visit the [Power Apps Community Forums](https://powerusers.microsoft.com/t5/Power-Apps-Community/ct-p/PowerApps1).
