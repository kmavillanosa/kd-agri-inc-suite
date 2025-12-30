# POS & Inventory Management System

## Welcome

Welcome to the documentation for the **Point of Sale (POS) and Inventory Management System** designed for KD Agri Inc Suite's cafe/restaurant/store operation.

## Overview

This system is designed to operate in a remote location with limited connectivity, providing a comprehensive solution for:

- **Point of Sale Operations**: Complete transaction processing with support for retail and wholesale pricing
- **Inventory Management**: Real-time stock tracking, low stock alerts, and supplier management
- **Sales Reporting**: Comprehensive analytics and financial reporting
- **User Management**: Role-based access control for staff (2-5 members)
- **Hardware Integration**: Barcode scanners, receipt printers, cash drawers, and payment card readers

## Key Features

### 🛒 Point of Sale
- Dynamic retail and wholesale pricing
- Multiple payment methods (Cash, Card, Mobile)
- Barcode scanning support
- Order cancellation and voiding
- Refund processing
- Receipt generation and printing

### 📦 Inventory Management
- Real-time stock tracking
- Low stock alerts
- Product variants and batch tracking
- Supplier and purchase order management
- Expiration date tracking

### 📊 Sales & Reporting
- Daily, weekly, monthly, and custom date range reports
- Sales by product, category, payment method, and pricing mode
- Export capabilities (CSV, PDF)
- Transaction history and audit trails

### 👥 User Management
- Three role levels: Cashier, Store Owner, Administrator
- Role-based permissions
- Activity tracking and audit logs

### 🔌 Hardware Integration
- Barcode scanners (USB, wireless, mobile camera)
- Receipt printers (thermal, impact, network)
- Cash drawers
- Payment card readers

## Technology Stack

- **Backend**: NestJS
- **Frontend**: Vite + React
- **Database**: Local database (SQLite/PostgreSQL/MySQL)
- **Deployment**: On-premise
- **Platform**: Web-based (mobile phones, tablets, desktops)

## System Characteristics

- ✅ **Offline-First**: Operates fully without internet connection
- ✅ **Web-Based**: Accessible on any device with a browser
- ✅ **Responsive Design**: Optimized for mobile, tablet, and desktop
- ✅ **Progressive Web App**: Can be installed on mobile devices
- ✅ **On-Premise**: No cloud dependency required

## Documentation Structure

This documentation is organized into the following sections:

1. **Functional Requirements**: Complete specification of all system features and capabilities
2. **System Architecture**: Technical stack and deployment information
3. **User Roles**: Permissions and access control
4. **Business Rules**: Operational rules and constraints

## Quick Links

- [Functional Requirements](functional-requirements.md) - Complete system specification
- [Project Overview](functional-requirements.md#1-project-overview) - Business context and stakeholders
- [System Architecture](functional-requirements.md#2-system-architecture) - Technical details

## Stakeholders

- **[Redacted]**: Head of Corporation, General Decision Maker
- **[Redacted]**: Board Member/Secretary
- **[Redacted]**: Board Member / Developer

---

*Last Updated: {{ git_revision_date_localized }}*

