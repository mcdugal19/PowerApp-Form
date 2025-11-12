# Power Apps Form - Structure Documentation

## Overview
This is a Microsoft Power Apps application structured for import into the Power Platform. The app follows the standard .msapp file structure.

## Project Structure

```
PowerApp-Form/
├── CanvasManifest.json          # Main app manifest with metadata
├── Properties.json               # App properties and configuration
├── Header.json                   # Version and structure information
├── README.md                     # Project description
├── POWERAPP_STRUCTURE.md         # This documentation file
│
├── AppCheckerResult.sarif/       # App checker validation results
├── CanvasManifest/               # Additional manifest files
├── Connections/                  # Data source connections
├── Controls/                     # Custom controls
├── DataSources/                  # Data source definitions
├── Other/                        # Additional resources
│
├── References/                   # App references
│   ├── DataSources.json         # Data source references
│   ├── Resources.json           # Resource references
│   └── Themes.json              # Theme configuration
│
└── Src/                         # Source code
    ├── Screen1.fx.yaml          # Main screen definition
    └── EditorState/             # Editor state files
        └── Screen1.editorstate.json

```

## File Descriptions

### Root Level Files

#### CanvasManifest.json
Contains the main manifest for the Power App including:
- Format version
- App properties (Name, ID, Author)
- Screen order
- Publish order indices

#### Properties.json
Defines app-wide properties:
- App version and creation source
- Document layout (dimensions, orientation)
- Background color
- Instrumentation settings
- Default behaviors

#### Header.json
Specifies version information:
- Document version
- Minimum version to load
- MSApp structure version

### Src/ Directory

Contains all screen definitions and logic written in Power Fx (YAML format).

#### Screen1.fx.yaml
The main form screen with:
- **Header Label**: Form title with blue background
- **Name Input**: Text field for name entry
- **Email Input**: Text field for email entry
- **Message Input**: Multi-line text area for messages
- **Submit Button**: Button with success notification on click
- **Status Label**: For displaying form status

### References/ Directory

#### DataSources.json
Empty initially - will contain references to connected data sources like:
- SharePoint lists
- Excel tables
- SQL databases
- Custom connectors

#### Resources.json
Empty initially - will contain app resources like:
- Images
- Media files
- Custom fonts

#### Themes.json
Contains theme configuration (currently set to System theme)

## How to Use This App

### For Development:

1. **Edit in Power Apps Studio**:
   - Open Power Apps Studio
   - Click "Open" → "Browse"
   - Navigate to this folder
   - The app will be loaded for editing

2. **Modify Screens**:
   - Edit `Src/Screen1.fx.yaml` to change the form layout
   - Add new screens by creating additional `.fx.yaml` files
   - Update `CanvasManifest.json` to include new screens

3. **Add Data Sources**:
   - Connect to data sources in Power Apps Studio
   - Connections will be saved in the Connections/ directory
   - Update DataSources.json with connection details

### For Import into Power Platform:

1. **Package the App**:
   ```bash
   # Zip the entire PowerApp-Form directory
   zip -r PowerApp-Form.msapp *
   ```

2. **Import to Power Apps**:
   - Go to make.powerapps.com
   - Click "Apps" → "Import canvas app"
   - Upload the PowerApp-Form.msapp file
   - Configure environment settings
   - Click "Import"

### For Version Control:

This structure is designed to work with Git:
- Each file is human-readable (JSON/YAML)
- Changes can be tracked and reviewed
- Multiple developers can collaborate
- Use `.gitignore` for sensitive connection strings

## Current Form Features

The default form includes:
- ✅ Responsive layout
- ✅ Name input field
- ✅ Email input field
- ✅ Multi-line message field
- ✅ Submit button with notification
- ✅ Clean, professional design
- ✅ Mobile-friendly (portrait orientation)

## Customization Guide

### Change Form Title:
Edit `Src/Screen1.fx.yaml`:
```yaml
HeaderLabel As label:
    Text: ="Your New Title Here"
```

### Add New Input Field:
Add to `Src/Screen1.fx.yaml`:
```yaml
PhoneLabel As label:
    Height: =40
    Text: ="Phone:"
    Width: =Parent.Width
    X: =20
    Y: =500
    
PhoneInput As text:
    Height: =50
    Width: =Parent.Width - 40
    X: =20
    Y: =540
    HintText: ="Enter phone number"
```

### Change Color Scheme:
Modify color values in `Src/Screen1.fx.yaml`:
```yaml
Fill: =RGBA(R, G, B, Alpha)  # Replace with your colors
```

### Submit to Data Source:
Modify the button's OnSelect in `Src/Screen1.fx.yaml`:
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
    Notify("Form submitted!", NotificationType.Success)
```

## Power Fx Language

Power Apps uses Power Fx, a low-code formula language:
- Similar to Excel formulas
- Strongly typed and declarative
- Formulas start with `=`
- Built-in functions for data manipulation

### Common Functions:
- `Notify()` - Display notifications
- `Patch()` - Update data sources
- `Navigate()` - Switch between screens
- `Filter()` - Filter collections
- `LookUp()` - Find specific records

## Next Steps

1. **Add Data Storage**: Connect to SharePoint, Dataverse, or SQL
2. **Add Validation**: Implement input validation rules
3. **Add More Screens**: Create multi-page forms
4. **Add Images**: Upload company logo or icons
5. **Configure Themes**: Create custom color schemes
6. **Add Security**: Implement user authentication

## Resources

- [Power Apps Documentation](https://docs.microsoft.com/powerapps/)
- [Power Fx Documentation](https://docs.microsoft.com/power-platform/power-fx/)
- [Canvas App Formula Reference](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)

## Version Information

- **App Version**: 2024-11-12T20:25:00.000Z
- **Doc Version**: 1.333
- **Min Version**: 1.331
- **Structure Version**: 2.0
