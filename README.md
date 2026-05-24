# Billing Application - VB6 & MS Access

A comprehensive desktop billing application built with Visual Basic 6.0 and Microsoft Access database.

## Features

### Core Functionality
- **Invoice Management**: Create, edit, and delete invoices with automatic number generation
- **Customer Management**: Maintain customer database with contact details and credit limits
- **Product/Service Catalog**: Manage products and services with pricing and tax codes
- **Payment Tracking**: Track payments, outstanding amounts, and payment history
- **Reports**: Generate detailed billing reports (Daily, Monthly, Yearly)
- **Database**: Built-in MS Access database with normalized schema
- **User-Friendly Interface**: Clean and intuitive GUI with menu-driven navigation

### Advanced Features
- **Role-Based Access Control**: Admin, Manager, and User roles
- **Tax Calculation**: Automatic tax computation per invoice item
- **Multi-Currency Support**: Handle different currencies (planned)
- **Payment Reminders**: Automatic alerts for overdue invoices
- **Database Backup**: Built-in backup and restore functionality
- **Audit Trail**: Complete transaction history and logging
- **Export to PDF**: Generate and export invoices and reports

## System Requirements

- **Operating System**: Windows 7/8/10/11
- **Visual Basic 6.0 Runtime**: Required for application execution
- **Microsoft Access**: 2003 or later (for database access)
- **.NET Framework**: 4.5 or higher
- **Disk Space**: 200 MB minimum
- **RAM**: 2 GB minimum
- **Processor**: Intel Pentium 4 or equivalent

## Quick Start Guide

### Installation

1. **Download the Installer**
   - Visit the Releases page
   - Download `BillingApp-Setup.exe` (latest version)

2. **Run Installation Wizard**
   - Double-click the installer
   - Choose installation directory (default: C:\Program Files\BillingApp)
   - Select Start Menu shortcuts
   - Choose desktop shortcut option

3. **Complete Setup**
   - Click "Finish"
   - Database will initialize on first run
   - Default admin account created

4. **First Login**
   - Username: `admin`
   - Password: `admin123`
   - **Important**: Change password immediately after first login

### User Manual

Complete documentation available in `docs/USER_MANUAL.md`:
- Step-by-step usage instructions
- Screenshots and examples
- Troubleshooting guide
- Keyboard shortcuts
- Best practices

## Project Structure

```
billing-app-vb6/
│
├── src/                       # Source code directory
│   ├── Forms/                 # VB6 Form files
│   │   ├── frmLogin.frm      # Login screen
│   │   ├── frmDashboard.frm  # Main dashboard
│   │   ├── frmCustomer.frm   # Customer management
│   │   ├── frmInvoice.frm    # Invoice creation/editing
│   │   ├── frmPayment.frm    # Payment recording
│   │   └── frmReports.frm    # Report generation
│   │
│   ├── Modules/              # VB6 Module files
│   │   ├── modMain.bas       # Main module/entry point
│   │   ├── modDatabase.bas   # Database connection functions
│   │   ├── modInvoice.bas    # Invoice business logic
│   │   ├── modCustomer.bas   # Customer operations
│   │   ├── modPayment.bas    # Payment processing
│   │   └── modReports.bas    # Report generation
│   │
│   ├── Classes/              # VB6 Class modules
│   │   ├── clsCustomer.cls   # Customer class definition
│   │   ├── clsInvoice.cls    # Invoice class definition
│   │   ├── clsPayment.cls    # Payment class definition
│   │   └── clsDatabase.cls   # Database wrapper class
│   │
│   ├── BillingApp.vbp        # VB6 Project file
│   ├── BillingApp.exe        # Compiled executable
│   └── SETUP_GUIDE.md        # Development setup instructions
│
├── database/                 # Database files
│   ├── BillingDB.mdb         # Main Access database
│   └── BillingDB.mdb.backup  # Backup copy
│
├── docs/                     # Documentation
│   ├── USER_MANUAL.md        # End-user documentation
│   ├── DATABASE_SCHEMA.md    # Database structure details
│   ├── ADMIN_MANUAL.md       # Administrator guide
│   └── API_REFERENCE.md      # Function reference
│
├── installer/               # Installer package
│   ├── BillingApp-Setup.exe  # Windows installer
│   └── BillingApp.iss        # Inno Setup script
│
├── tests/                   # Test files
│   ├── test_invoice.bas     # Invoice module tests
│   └── test_database.bas    # Database connection tests
│
├── README.md                # This file
├── CHANGELOG.md             # Version history
├── LICENSE                  # MIT License
└── CONTRIBUTING.md          # Contribution guidelines
```

## Database Schema

### Core Tables

**Customers**
- CustomerID (Primary Key)
- Customer Name, Contact Person
- Email, Phone, Address
- City, State, Postal Code, Country
- Tax ID, Credit Limit, Outstanding Balance

**Products**
- ProductID (Primary Key)
- Product Name, Description, Category
- Unit Price, Tax Rate, HSN Code
- Stock Quantity, Supplier Information

**Invoices**
- InvoiceID (Primary Key)
- Invoice Number, Customer ID
- Invoice Date, Due Date
- Subtotal, Tax Amount, Total Amount
- Paid Amount, Status (Draft/Sent/Paid/Overdue)

**InvoiceItems**
- ItemID (Primary Key)
- Invoice ID, Product ID
- Quantity, Unit Price, Tax Amount
- Line Total, Item Total

**Payments**
- PaymentID (Primary Key)
- Invoice ID, Payment Date, Amount
- Payment Method, Reference Number
- Recorded By, Date Created

**Users**
- UserID (Primary Key)
- Username, Password (Encrypted)
- Full Name, Email, Role
- Is Active, Date Created

For detailed schema information, see `docs/DATABASE_SCHEMA.md`

## Key Features Explained

### Invoice Management
- Create invoices with automatic numbering
- Add multiple line items with auto-calculated totals
- Tax automatically computed based on product rates
- Edit only draft invoices
- Send invoices via email or print
- Mark as paid when payment received

### Customer Management
- Add new customers with complete details
- Assign credit limits
- Track outstanding balance
- Maintain contact history
- View customer-wise transaction history

### Payment Processing
- Record payments (Cash, Check, Card, Bank Transfer)
- Partial payment support
- Automatic invoice status update
- Generate payment receipts
- Payment history and tracking

### Reports
- **Daily Report**: Today's invoices and collections
- **Monthly Report**: Month summary with trends
- **Yearly Report**: Annual breakdown
- **Custom Reports**: Flexible date range and filters
- Export to PDF or Excel
- Print directly

## Development

### For Developers

#### Prerequisites
- Visual Basic 6.0 IDE
- Microsoft Access 2003+
- Windows SDK
- Git for Windows

#### Building from Source
1. Clone the repository: `git clone https://github.com/shuvamchak02-create/billing-app-vb6.git`
2. Open VB6 IDE
3. File → Open Project → Select `src/BillingApp.vbp`
4. Ensure database connection string is correct
5. Project → Make BillingApp.exe (to compile)

#### Creating Installer
1. Install Inno Setup
2. Edit `installer/BillingApp.iss`
3. Run Inno Setup Compiler
4. Select the .iss file
5. Click "Compile"

See `src/SETUP_GUIDE.md` for detailed development instructions.

## Usage Examples

### Creating Your First Invoice
```
1. Open Billing Application
2. Click "Invoices" → "New Invoice"
3. Select Customer from dropdown
4. Click "Add Item"
5. Select Product and enter quantity
6. Tax auto-calculated
7. Review totals
8. Click "Save Invoice"
```

### Recording a Payment
```
1. Click "Payments" → "Record Payment"
2. Select Invoice to pay
3. Enter payment amount
4. Choose payment method
5. Enter reference number (if applicable)
6. Click "Save Payment"
7. Invoice status auto-updated to "Paid"
```

### Generating Monthly Report
```
1. Click "Reports" → "Monthly Report"
2. Select month and year
3. Review summary data
4. Click "Export to PDF" or "Print"
5. Choose location to save
```

## Troubleshooting

### Common Issues & Solutions

**Issue**: Application won't start
- **Solution**: Check VB6 runtime is installed. Download from microsoft.com if needed.

**Issue**: Database connection error
- **Solution**: Verify BillingDB.mdb exists in database folder. Run database repair utility if corrupted.

**Issue**: Login fails
- **Solution**: Ensure Caps Lock is off. Reset password using admin account if needed.

**Issue**: Printing errors
- **Solution**: Check printer is online. Update printer drivers. Verify print spooler service running.

**Issue**: Slow performance
- **Solution**: Close other applications. Check available disk space. Compact database (Tools → Compact Database).

For more troubleshooting, see `docs/USER_MANUAL.md`

## Support & Feedback

### Getting Help
- 📖 **Documentation**: See `docs/` folder
- 🐛 **Bug Reports**: GitHub Issues
- 💡 **Feature Requests**: GitHub Discussions
- 📧 **Email**: support@billingapp.dev

### Contributing
We welcome contributions! Please see `CONTRIBUTING.md` for guidelines.

## Changelog

### Version 1.0.0 (May 24, 2026) - Initial Release
- Complete invoice management system
- Customer and product database
- Payment tracking module
- Report generation system
- User authentication
- Database backup/restore

### Planned Features (Future Versions)
- Email integration
- SMS notifications
- Mobile app companion
- Cloud backup
- API integration
- Multi-currency support
- Advanced analytics

See `CHANGELOG.md` for detailed version history.

## License

This project is licensed under the MIT License - see `LICENSE` file for details.

## Project Information

- **Version**: 1.0.0
- **Author**: Billing Application Development Team
- **Last Updated**: May 24, 2026
- **Repository**: https://github.com/shuvamchak02-create/billing-app-vb6
- **Status**: Actively Maintained

## Acknowledgments

- Visual Basic 6.0 Community
- Microsoft Access Development Resources
- Contributors and Testers

---

**Questions?** Open an issue on GitHub or check the documentation in the `docs/` folder.

**Want to contribute?** Check `CONTRIBUTING.md` for guidelines.

**Found a bug?** Report it on GitHub Issues with detailed information.

---

**Made with ❤️ for the VB6 Community**
