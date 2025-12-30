# Functional Requirements Document - POS and Inventory Management System

## 1. Project Overview

### 1.1 Purpose

This document defines the functional requirements for a Point of Sale (POS) and Inventory Management System designed for a cafe/restaurant/store operating in a remote location. The system must operate primarily offline with optional online synchronization capabilities.

### 1.2 Business Context

- **Location**: Remote area with limited connectivity
- **Business Type**: Cafe/Restaurant/Store with unique attractions (rabbit breeding, soft-shell crabs)
- **Products**: Cooked food, beverages, and specialty items
- **Staff Size**: Limited to 2-5 staff members (no shift management required)
- **Future Expansion**: Open backyard area planned for business center development

### 1.3 Stakeholders

- **[Redacted]**: Head of Corporation, General Decision Maker
- **[Redacted]**: Board Member/Secretary
- **[Redacted]**: Board Member / Developer

## 2. System Architecture

### 2.1 Technology Stack

- **Backend**: NestJS
- **Frontend**: Vite + React
- **Database**: Local database (SQLite/PostgreSQL/MySQL) for on-premise storage
- **Deployment**: On-premise (local server/network)
- **Connectivity**: Offline-first with optional online synchronization

### 2.2 System Characteristics

- Web-based application for cross-platform compatibility
- Responsive design supporting mobile phones, tablets, and desktop computers
- Offline-first architecture with local data storage
- Optional online synchronization when connectivity is available
- Single or multi-device deployment (mobile phones, tablets, and desktop computers)
- Hardware integration: Barcode scanner and receipt printer support
- Progressive Web App (PWA) capabilities for mobile device installation

### 2.3 Hardware Requirements

- **Barcode Scanner**: USB or wireless barcode scanner for product identification (see Section 4.7.1). On mobile phones, can use device camera for barcode scanning
- **Receipt Printer**: Thermal or impact receipt printer for generating paper receipts (see Section 4.7.2)
- **Cash Drawer**: Electronic cash drawer (optional, can be triggered by receipt printer or manually)
- **Card Reader**: Payment card reader for credit/debit card processing (optional)
- **Paper Trail**: All sales transactions can generate physical receipts for audit and record-keeping purposes

## 3. User Roles and Permissions

### 3.1 Cashier

- Process sales transactions
- Generate invoices/receipts
- View product catalog
- Process payments (cash, card, mobile payments)
- View transaction history (limited to own transactions)
- Cancel orders before sale completion
- Access retail pricing mode (default)
- Access wholesale pricing mode (if authorized)

### 3.2 Store Owner

- All Cashier permissions
- View low stock alerts
- Manage inventory content
- Add/update stock quantities
- View sales reports and analytics
- View total sales and financial computations
- Manage product catalog
- Void completed transactions
- View voided transactions
- Access wholesale pricing mode (always authorized)
- Configure retail and wholesale prices for products

### 3.3 Administrator

- All Store Owner permissions
- Full system access and management
- User management (add, remove, modify users)
- Role and permission management
- Audit log viewing (track all user actions)
- System configuration
- Data synchronization management

## 4. Functional Requirements

### 4.1 Point of Sale (POS) Module

#### 4.1.1 Product Selection

- **FR-POS-001**: System shall allow cashiers to browse and search product catalog
- **FR-POS-002**: System shall display product name, price, and availability status
- **FR-POS-003**: System shall support dynamic pricing mode selection (retail or wholesale)
- **FR-POS-004**: System shall display appropriate price (retail or wholesale) based on selected pricing mode
- **FR-POS-005**: System shall allow authorized users to switch between retail and wholesale pricing modes
- **FR-POS-006**: System shall allow cashiers to add products to cart
- **FR-POS-007**: System shall support quantity modification for items in cart
- **FR-POS-008**: System shall allow removal of items from cart
- **FR-POS-009**: System shall display running total of cart items
- **FR-POS-010**: System shall display current pricing mode (retail/wholesale) in cart view
- **FR-POS-011**: System shall support barcode scanning for product identification
- **FR-POS-012**: System shall automatically add product to cart when barcode is scanned (using current pricing mode)
- **FR-POS-013**: System shall handle invalid or unrecognized barcode scans with appropriate error messages
- **FR-POS-014**: System shall support manual product entry as alternative to barcode scanning

#### 4.1.2 Checkout Process

- **FR-POS-015**: System shall allow cashiers to initiate checkout process
- **FR-POS-016**: System shall display pricing mode (retail/wholesale) during checkout
- **FR-POS-017**: System shall prevent changing pricing mode once checkout is initiated
- **FR-POS-018**: System shall support multiple payment methods:
- Cash
- Credit/Debit cards (via card reader integration)
- Mobile payments (QR code, NFC, etc.)
- **FR-POS-019**: System shall calculate change for cash transactions
- **FR-POS-020**: System shall process payment and complete sale
- **FR-POS-021**: System shall automatically update inventory upon sale completion
- **FR-POS-022**: System shall record pricing mode (retail/wholesale) for each transaction
- **FR-POS-023**: System shall support applying discounts to items or entire transaction
- **FR-POS-024**: System shall support percentage-based discounts
- **FR-POS-025**: System shall support fixed amount discounts
- **FR-POS-026**: System shall support promotional codes/coupons
- **FR-POS-027**: System shall calculate and apply taxes (if configured)
- **FR-POS-028**: System shall display itemized breakdown (subtotal, discounts, taxes, total)
- **FR-POS-029**: System shall apply discounts to retail or wholesale price based on current pricing mode

#### 4.1.3 Invoice/Receipt Generation

- **FR-POS-030**: System shall generate invoice/receipt upon sale completion
- **FR-POS-031**: Receipt shall include:
- Business name and contact information
- Transaction date and time
- Transaction ID/Number
- List of items purchased with quantities and prices
- Pricing mode indicator (Retail/Wholesale)
- Discounts applied (if any)
- Subtotal, taxes (if applicable), and total
- Payment method and amount
- Change given (for cash transactions)
- **FR-POS-032**: System can generate and print physical receipt upon sale completion (optional, configurable)
- **FR-POS-033**: System shall support digital receipt display on screen
- **FR-POS-034**: System shall allow reprinting of receipts for completed transactions
- **FR-POS-035**: System shall integrate with receipt printer hardware
- **FR-POS-036**: System shall detect receipt printer connection status
- **FR-POS-037**: System shall handle printer errors gracefully (offline, paper out, etc.)
- **FR-POS-038**: System shall queue receipt printing if printer is temporarily unavailable
- **FR-POS-039**: System shall maintain receipt print history for audit purposes
- **FR-POS-040**: System shall support triggering cash drawer opening (if connected) upon receipt printing

#### 4.1.4 Order Cancellation and Voiding

- **FR-POS-041**: System shall allow cancellation of orders before sale completion
- **FR-POS-042**: System shall clear cart and reset transaction when order is cancelled
- **FR-POS-043**: System shall allow voiding of completed transactions
- **FR-POS-044**: System shall require authorization (Store Owner or Administrator) for voiding transactions
- **FR-POS-045**: System shall restore inventory quantities when transaction is voided
- **FR-POS-046**: System shall generate void receipt/documentation when transaction is voided
- **FR-POS-047**: System shall record reason for voiding transaction
- **FR-POS-048**: System shall maintain record of all voided transactions
- **FR-POS-049**: System shall display voided transactions distinctly in transaction history
- **FR-POS-050**: System shall allow voiding of individual items within a completed transaction (partial void) - requires Store Owner or Administrator authorization
- **FR-POS-051**: System shall update inventory accordingly when items are partially voided
- **FR-POS-052**: System shall support configurable time limit for voiding transactions (optional, can be disabled)

#### 4.1.5 Refunds

- **FR-POS-053**: System shall support processing refunds for completed transactions
- **FR-POS-054**: System shall require authorization (Store Owner or Administrator) for processing refunds
- **FR-POS-055**: System shall support full refunds (entire transaction)
- **FR-POS-056**: System shall support partial refunds (individual items)
- **FR-POS-057**: System shall restore inventory quantities for refunded items
- **FR-POS-058**: System shall record refund reason and amount
- **FR-POS-059**: System shall generate refund receipt/documentation
- **FR-POS-060**: System shall process refund to original payment method when possible
- **FR-POS-061**: System shall support cash refunds for original cash transactions
- **FR-POS-062**: System shall maintain record of all refunded transactions
- **FR-POS-063**: System shall maintain original pricing mode (retail/wholesale) in refund records

### 4.2 Inventory Management Module

#### 4.2.1 Stock Monitoring

- **FR-INV-001**: System shall track inventory levels for all products
- **FR-INV-002**: System shall display current stock quantities
- **FR-INV-003**: System shall provide low stock alerts/notifications
- **FR-INV-004**: System shall allow configurable low stock thresholds per product
- **FR-INV-005**: System shall display products with low stock in a dedicated view
- **FR-INV-006**: System shall update stock levels in real-time upon sales

#### 4.2.2 Stock Management

- **FR-INV-007**: Store owners shall be able to add new stock to existing products
- **FR-INV-008**: System shall support stock adjustments (increase/decrease)
- **FR-INV-009**: System shall maintain stock adjustment history
- **FR-INV-010**: System shall support bulk stock updates
- **FR-INV-011**: System shall track stock movements (in/out)
- **FR-INV-028**: System shall support receiving stock from suppliers
- **FR-INV-029**: System shall support purchase order creation
- **FR-INV-030**: System shall track purchase orders and their status
- **FR-INV-031**: System shall support supplier/vendor management
- **FR-INV-032**: System shall record supplier information (name, contact, etc.)
- **FR-INV-033**: System shall link received stock to purchase orders
- **FR-INV-034**: System shall support cost tracking per supplier

#### 4.2.3 Product Management

- **FR-INV-012**: Store owners shall be able to add new products to catalog
- **FR-INV-013**: Store owners shall be able to edit product information:
- Product name
- Description
- Retail price
- Wholesale price
- Category
- Initial stock quantity
- Low stock threshold
- Barcode/SKU
- Unit of measure (pieces, kg, liters, etc.)
- Expiration date (if applicable)
- Batch/lot number (if applicable)
- **FR-INV-014**: Store owners shall be able to deactivate/remove products
- **FR-INV-015**: System shall support product categories
- **FR-INV-016**: System shall support product images
- **FR-INV-017**: System shall generate unique barcode for each product
- **FR-INV-018**: System shall support manual barcode entry for products
- **FR-INV-019**: System shall validate barcode uniqueness
- **FR-INV-020**: System shall support barcode label printing for products
- **FR-INV-021**: System shall display barcode in product management interface
- **FR-INV-022**: System shall support product variants (sizes, colors, options)
- **FR-INV-023**: System shall track inventory by variant if applicable
- **FR-INV-024**: System shall support multiple units of measure per product
- **FR-INV-025**: System shall track expiration dates for perishable items
- **FR-INV-026**: System shall provide alerts for items nearing expiration
- **FR-INV-027**: System shall support batch/lot tracking for inventory items
- **FR-INV-035**: System shall support separate retail and wholesale pricing for each product
- **FR-INV-036**: System shall allow products to have only retail price (wholesale price optional)
- **FR-INV-037**: System shall allow products to have only wholesale price (retail price optional)
- **FR-INV-038**: System shall display both retail and wholesale prices in product management interface
- **FR-INV-039**: System shall validate that wholesale price is typically lower than retail price (warning, not enforced)

### 4.3 Sales and Reporting Module

#### 4.3.1 Sales Tracking

- **FR-SALES-001**: System shall record all completed transactions
- **FR-SALES-002**: System shall track sales by:
- Date and time
- Cashier/user
- Payment method
- Product/item
- Transaction status (completed, voided, cancelled)
- Pricing mode (retail/wholesale)
- **FR-SALES-003**: System shall maintain complete sales history including voided, cancelled, and refunded transactions
- **FR-SALES-004**: System shall distinguish between voided, refunded, and active transactions in sales reports
- **FR-SALES-005**: System shall allow filtering of sales reports to exclude voided/refunded transactions

#### 4.3.2 Sales Reports

- **FR-SALES-006**: Store owners shall be able to view total sales
- **FR-SALES-007**: System shall provide sales reports by:
- Daily sales
- Weekly sales
- Monthly sales
- Custom date range
- **FR-SALES-008**: System shall calculate and display:
- Total revenue
- Number of transactions
- Average transaction value
- Sales by product
- Sales by category
- Sales by payment method
- Sales by pricing mode (retail vs wholesale)
- Retail revenue vs wholesale revenue
- Discounts applied
- Taxes collected
- Refunds processed
- **FR-SALES-009**: System shall support export of sales data (CSV, PDF)
- **FR-SALES-010**: System shall provide sales reports by cashier/user

### 4.4 User Management Module

#### 4.4.1 User Administration

- **FR-USER-001**: Administrators shall be able to create new users
- **FR-USER-002**: Administrators shall be able to edit user information
- **FR-USER-003**: Administrators shall be able to deactivate/remove users
- **FR-USER-004**: System shall support user roles (Cashier, Store Owner, Administrator)
- **FR-USER-005**: System shall enforce role-based access control

#### 4.4.2 Access Control

- **FR-USER-006**: Administrators shall be able to assign roles to users
- **FR-USER-007**: Administrators shall be able to modify user permissions
- **FR-USER-008**: System shall require authentication for all system access
- **FR-USER-009**: System shall support password management (change, reset)
- **FR-USER-010**: System shall support user profile management (name, contact, etc.)
- **FR-USER-011**: System shall limit total number of users to 2-5 staff members
- **FR-USER-012**: System shall support user activity tracking

### 4.5 Audit and Activity Logging

#### 4.5.1 Activity Tracking

- **FR-AUDIT-001**: System shall log all user actions
- **FR-AUDIT-002**: Logs shall include:
- User identification
- Action performed
- Timestamp
- Affected data/records
- **FR-AUDIT-003**: Administrators shall be able to view audit logs
- **FR-AUDIT-004**: System shall support filtering audit logs by:
- User
- Date range
- Action type
- **FR-AUDIT-005**: System shall maintain audit log history
- **FR-AUDIT-006**: System shall log all order cancellations with user and timestamp
- **FR-AUDIT-007**: System shall log all transaction voids with user, timestamp, reason, and affected transaction details

### 4.8 System Configuration and Setup

#### 4.8.1 Initial Setup

- **FR-CFG-001**: System shall support initial system setup and configuration
- **FR-CFG-002**: System shall require administrator account creation during setup
- **FR-CFG-003**: System shall support business information configuration (name, address, contact, tax ID, etc.)
- **FR-CFG-004**: System shall support tax rate configuration
- **FR-CFG-005**: System shall support receipt format customization during setup
- **FR-CFG-006**: System shall support hardware device configuration and testing

#### 4.8.2 Tax Management

- **FR-CFG-007**: Administrators shall be able to configure tax rates
- **FR-CFG-008**: System shall support multiple tax rates (e.g., sales tax, VAT)
- **FR-CFG-009**: System shall support tax-exempt products or categories
- **FR-CFG-010**: System shall apply taxes automatically based on product configuration
- **FR-CFG-011**: System shall display tax breakdown on receipts

#### 4.8.3 Discount and Promotion Management

- **FR-CFG-012**: Administrators shall be able to create and manage discount rules
- **FR-CFG-013**: System shall support time-based promotions
- **FR-CFG-014**: System shall support product-specific discounts
- **FR-CFG-015**: System shall support category-based discounts
- **FR-CFG-016**: System shall support promotional code management

#### 4.8.4 Pricing Mode Configuration

- **FR-CFG-017**: Administrators shall be able to configure default pricing mode (retail/wholesale)
- **FR-CFG-018**: Administrators shall be able to assign wholesale pricing access to specific cashiers
- **FR-CFG-019**: System shall support per-user pricing mode permissions
- **FR-CFG-020**: System shall allow Store Owners and Administrators to always access wholesale pricing

### 4.9 Customer Management

#### 4.9.1 Customer Information

- **FR-CUST-001**: System shall support optional customer information capture
- **FR-CUST-002**: System shall allow storing customer name and contact information
- **FR-CUST-003**: System shall link transactions to customers (optional)
- **FR-CUST-004**: System shall support customer search and lookup
- **FR-CUST-005**: System shall maintain customer transaction history

### 4.10 Data Management

#### 4.10.1 Backup and Recovery

- **FR-DATA-001**: System shall support automated data backups
- **FR-DATA-002**: System shall support manual backup creation
- **FR-DATA-003**: System shall support data restoration from backups
- **FR-DATA-004**: Administrators shall be able to configure backup schedules
- **FR-DATA-005**: System shall store backups locally or on network storage

#### 4.10.2 Data Retention and Archival

- **FR-DATA-006**: System shall support configurable data retention policies
- **FR-DATA-007**: System shall support archival of old transactions
- **FR-DATA-008**: System shall maintain archived data for audit purposes
- **FR-DATA-009**: System shall support data export for long-term storage

### 4.6 Offline and Synchronization

#### 4.6.1 Offline Operation

- **FR-SYNC-001**: System shall operate fully offline without internet connection
- **FR-SYNC-002**: System shall store all data locally
- **FR-SYNC-003**: System shall queue transactions when offline
- **FR-SYNC-004**: System shall detect connectivity status

#### 4.6.2 Data Synchronization

- **FR-SYNC-005**: System shall support optional online synchronization
- **FR-SYNC-006**: When connectivity is available, system shall sync data
- **FR-SYNC-007**: System shall handle sync conflicts using last-write-wins or manual resolution
- **FR-SYNC-010**: System shall support conflict resolution strategies (automatic or manual)
- **FR-SYNC-011**: System shall notify administrators of sync conflicts requiring attention
- **FR-SYNC-008**: Administrators shall be able to manually trigger synchronization
- **FR-SYNC-009**: System shall provide sync status indicators

### 4.7 Hardware Integration Module

#### 4.7.1 Barcode Scanner Integration

- **FR-HW-001**: System shall support USB barcode scanner connectivity
- **FR-HW-002**: System shall support wireless/Bluetooth barcode scanner connectivity
- **FR-HW-003**: System shall support mobile device camera for barcode scanning (on mobile phones)
- **FR-HW-004**: System shall detect barcode scanner connection status
- **FR-HW-005**: System shall process barcode input in real-time
- **FR-HW-006**: System shall handle multiple barcode formats (UPC, EAN, Code 128, QR codes, etc.)
- **FR-HW-007**: System shall provide visual/audio feedback upon successful barcode scan
- **FR-HW-008**: System shall allow configuration of barcode scanner settings
- **FR-HW-009**: System shall request camera permissions on mobile devices for barcode scanning
- **FR-HW-010**: System shall provide fallback to manual entry if camera/scanner is unavailable

#### 4.7.2 Receipt Printer Integration

- **FR-HW-011**: System shall support thermal receipt printer connectivity
- **FR-HW-012**: System shall support impact/dot-matrix receipt printer connectivity
- **FR-HW-013**: System shall support network/wireless receipt printers for mobile device connectivity
- **FR-HW-014**: System shall detect receipt printer connection status
- **FR-HW-015**: System shall support standard receipt printer protocols (ESC/POS, etc.)
- **FR-HW-016**: System shall handle printer queue management
- **FR-HW-017**: System shall provide printer status monitoring (paper level, connectivity, errors)
- **FR-HW-018**: System shall allow configuration of receipt printer settings (paper width, print density, etc.)
- **FR-HW-019**: System shall support receipt format customization (header, footer, logo)
- **FR-HW-020**: System shall ensure receipt printing works in offline mode
- **FR-HW-021**: System shall support sharing receipt as PDF/image from mobile devices when printer is unavailable

#### 4.7.3 Cash Drawer Integration

- **FR-HW-022**: System shall support electronic cash drawer connectivity
- **FR-HW-023**: System shall trigger cash drawer opening upon receipt printing (if configured)
- **FR-HW-024**: System shall support manual cash drawer opening
- **FR-HW-025**: System shall detect cash drawer connection status
- **FR-HW-026**: System shall support cash counting and reconciliation
- **FR-HW-027**: System shall support network/wireless cash drawer for mobile device connectivity

#### 4.7.4 Payment Card Reader Integration

- **FR-HW-028**: System shall support payment card reader connectivity (USB, serial, or network)
- **FR-HW-029**: System shall support mobile card readers (Bluetooth, audio jack, or Lightning/USB-C connected)
- **FR-HW-030**: System shall process card payments through integrated card reader
- **FR-HW-031**: System shall handle card payment authorization
- **FR-HW-032**: System shall detect card reader connection status
- **FR-HW-033**: System shall support multiple card reader protocols (EMV, NFC, etc.)
- **FR-HW-034**: System shall support mobile device NFC for contactless payments

## 5. Non-Functional Requirements

### 5.1 Performance

- **NFR-001**: System shall respond to user actions within 2 seconds under normal load
- **NFR-002**: System shall support concurrent users (minimum 5 simultaneous users, aligned with 2-5 staff size)
- **NFR-003**: System shall handle at least 1000 products in catalog

### 5.2 Reliability

- **NFR-004**: System shall have 99% uptime during business hours
- **NFR-005**: System shall have data backup and recovery mechanisms (see Section 4.10.1)
- **NFR-018**: System shall support automated daily backups
- **NFR-019**: System shall support backup verification and integrity checks
- **NFR-006**: System shall prevent data loss during power outages

### 5.3 Usability

- **NFR-007**: System shall have intuitive user interface
- **NFR-008**: System shall be accessible on mobile phones, tablets, and desktop computers
- **NFR-009**: System shall support touch and mouse/keyboard interactions
- **NFR-010**: System shall provide clear error messages
- **NFR-020**: System shall provide responsive user interface optimized for mobile phone screens
- **NFR-021**: System shall support touch interactions on mobile devices
- **NFR-022**: System shall work in mobile web browsers (Chrome, Safari, Firefox, etc.)
- **NFR-023**: System shall support Progressive Web App (PWA) installation on mobile devices
- **NFR-024**: System shall provide mobile-optimized layouts for POS operations
- **NFR-025**: System shall support offline functionality on mobile devices

### 5.4 Security

- **NFR-011**: System shall require user authentication
- **NFR-012**: System shall encrypt sensitive data
- **NFR-013**: System shall maintain secure session management
- **NFR-014**: System shall protect against unauthorized access

### 5.5 Deployment

- **NFR-015**: System shall be deployable on-premise
- **NFR-016**: System shall not require cloud services for core functionality
- **NFR-017**: System shall support local network deployment

## 6. Business Rules

### 6.1 Sales Rules

- **BR-001**: A sale cannot be completed if product is out of stock
- **BR-002**: Inventory must be decremented immediately upon sale completion
- **BR-003**: All sales must be associated with a cashier/user

### 6.2 Inventory Rules

- **BR-004**: Stock quantities cannot be negative
- **BR-005**: Low stock alerts trigger when stock falls below configured threshold
- **BR-006**: Stock adjustments must be logged with user and timestamp

### 6.3 User Rules

- **BR-007**: At least one administrator account must exist
- **BR-008**: Users cannot delete their own account
- **BR-009**: Deactivated users cannot log in

### 6.4 Receipt and Paper Trail Rules

- **BR-010**: Every completed sale can generate a physical paper receipt
- **BR-011**: Sale can be completed with or without physical receipt printing
- **BR-012**: All receipts must be stored digitally for reprinting capability
- **BR-013**: Receipt reprints must be clearly marked as reprints in the receipt content

### 6.5 Order Cancellation and Voiding Rules

- **BR-014**: Orders can be cancelled at any time before sale completion without authorization
- **BR-015**: Completed transactions can only be voided by Store Owner or Administrator
- **BR-016**: Partial voids require Store Owner or Administrator authorization
- **BR-017**: Voiding a transaction must restore inventory quantities to pre-sale levels
- **BR-018**: All voided transactions must be logged with user, timestamp, and reason
- **BR-019**: Voided transactions must remain in system records for audit purposes
- **BR-020**: Voided transactions must be clearly marked as voided in reports and history
- **BR-021**: Partial voids must restore inventory only for voided items
- **BR-022**: Void receipts must be generated and can be printed for voided transactions

### 6.6 Refund Rules

- **BR-023**: Refunds can only be processed by Store Owner or Administrator
- **BR-024**: Refunding a transaction must restore inventory quantities for refunded items
- **BR-025**: All refunds must be logged with user, timestamp, reason, and amount
- **BR-026**: Refunded transactions must remain in system records for audit purposes
- **BR-027**: Refund receipts must be generated and can be printed

### 6.7 Tax and Discount Rules

- **BR-028**: Taxes must be calculated based on configured tax rates
- **BR-029**: Tax-exempt products or categories must not have taxes applied
- **BR-030**: Discounts cannot result in negative transaction totals
- **BR-031**: Promotional codes must be validated before application

### 6.8 Staff and User Rules

- **BR-032**: System shall support maximum of 2-5 staff members
- **BR-033**: No shift management is required (all staff work same hours)

### 6.9 Retail and Wholesale Pricing Rules

- **BR-034**: Products can have both retail and wholesale prices configured
- **BR-035**: Products can have only retail price (wholesale price is optional)
- **BR-036**: Products can have only wholesale price (retail price is optional)
- **BR-037**: Cashiers can access retail pricing mode by default
- **BR-038**: Cashiers require authorization to access wholesale pricing mode
- **BR-039**: Store Owners and Administrators always have access to wholesale pricing mode
- **BR-040**: Pricing mode (retail/wholesale) must be selected before adding items to cart
- **BR-041**: Pricing mode cannot be changed once checkout is initiated
- **BR-042**: All transactions must record which pricing mode was used (retail or wholesale)
- **BR-043**: Receipts must display pricing mode indicator (Retail/Wholesale)
- **BR-044**: Sales reports must distinguish between retail and wholesale transactions
- **BR-045**: Wholesale price is typically lower than retail price (system may warn but not enforce)

## 7. Future Considerations

### 7.1 Planned Enhancements

- Business center expansion support
- Multi-location management
- Advanced analytics and forecasting
- Integration with accounting systems
- Customer management and loyalty programs

## 8. Assumptions and Constraints

### 8.1 Assumptions

- Local network infrastructure is available
- Devices (mobile phones, tablets, desktop) are available for deployment
- Users have basic computer literacy
- Power supply is available (with backup considerations)
- Barcode scanner hardware is available and compatible with deployment devices
- Receipt printer hardware is available and compatible with deployment devices
- Receipt paper and printer supplies are maintained and available
- Staff size is limited to 2-5 members (no shift management needed)
- Local database server is available for on-premise deployment
- Backup storage solution is available (local or network storage)

### 8.2 Constraints

- System must operate in remote location with limited connectivity
- On-premise deployment only (no cloud dependency)
- Must work offline as primary mode
- Budget and timeline constraints as defined by stakeholders

## 9. Glossary

- **POS**: Point of Sale
- **Offline-first**: System designed to work primarily without internet connection
- **On-premise**: Software installed and running on local servers/computers
- **Low stock threshold**: Minimum quantity before alert is triggered
- **Web-based Application**: Application accessible through web browsers, works on any device with a browser (mobile phones, tablets, desktops)
- **Progressive Web App (PWA)**: Web application that can be installed on mobile devices and works offline
- **Barcode**: Machine-readable representation of product identifier (UPC, EAN, Code 128, etc.)
- **Paper Trail**: Physical documentation (printed receipts) of sales transactions for audit and record-keeping (optional)
- **ESC/POS**: Standard command set for receipt printers (Epson Standard Code for Point of Sale)
- **Void**: Cancellation of a completed transaction that restores inventory and creates audit record
- **Refund**: Return of payment for a completed transaction, separate from voiding
- **Partial Void**: Voiding of individual items within a completed transaction
- **Batch/Lot Tracking**: Tracking inventory by batch or lot numbers for traceability
- **Unit of Measure**: Standard measurement unit for products (pieces, kg, liters, etc.)
- **Retail Price**: Standard price for individual customers purchasing products
- **Wholesale Price**: Discounted price typically for bulk purchases or business customers
- **Pricing Mode**: Current pricing context (retail or wholesale) that determines which price is used during transaction

