# Listing Engine Backend - Vacational Rental website wordpress plugin

A powerful WordPress admin plugin for managing vacation rental listing data through dedicated database tables and custom wp-admin interfaces.

**Plugin Version:** 2.5.8

---

## Table of Contents

- [Overview](#overview)
- [Who Should Use This Plugin](#who-should-use-this-plugin)
- [Key Features](#key-features)
- [Screenshots](#screenshots)
- [System Requirements](#system-requirements)
- [Technology Stack](#technology-stack)
- [Installation Guide](#installation-guide)
- [Getting Started](#getting-started)
- [Admin Modules](#admin-modules)
- [Database Schema](#database-schema)
- [How It Works](#how-it-works)
- [For Developers](#for-developers)
- [Extension Points](#extension-points)
- [Security](#security)
- [Troubleshooting](#troubleshooting)
- [Changelog](#changelog)
- [Support & Contact](#support--contact)
- [License](#license)

---

## Overview

**Listing Engine Backend** is a comprehensive WordPress plugin designed specifically for managing vacation rental listings. Unlike traditional WordPress approaches that rely on custom post types, this plugin maintains its own dedicated MySQL database schema for storing and managing all listing-related data.

The plugin provides a complete backend administration system that enables property managers to:

- Create and manage property types (Apartments, Villas, Cabins, etc.)
- Define amenities (WiFi, Pool, Parking, etc.)
- Set up locations/destinations
- Add and manage property listings with images and availability
- Handle blocked dates and availability management

This is an **admin-focused data management system** - it handles all the backend data operations but does not include a public frontend booking interface. This makes it perfect for developers who want to build their own custom frontend while having a robust backend already taken care of.

---

## Who Should Use This Plugin

### Property Managers & Rental Companies
- Vacation rental property managers handling multiple listings
- Property management companies needing centralized inventory control
- Rental businesses requiring structured data management
- Hosts managing properties across different locations

### Web Developers & Agencies
- Developers building custom vacation rental platforms
- Agencies creating client websites with property listings
- Developers who need a robust backend without a predefined frontend
- Those wanting to integrate with existing WordPress themes

### Use Cases
- Vacation home rental websites
- Holiday apartment directories
- Hotel or resort property management
- Real estate listing management
- Any website requiring structured property data

---

## Key Features

### 1. Dedicated Database Tables
- Uses custom MySQL tables instead of WordPress posts
- Six specialized tables for different data types
- Efficient data storage and retrieval
- No interference with WordPress core posts

### 2. Comprehensive Admin Interface
- Dedicated LEB menu in WordPress admin
- Five main admin modules: Types, Database, Amenities, Locations, Properties
- Clean, intuitive user interface
- AJAX-powered operations for smooth experience

### 3. Property Management
- Full CRUD operations for property listings
- Property gallery with drag-and-drop reordering
- Blocked dates management with calendar interface
- Property duplication feature
- Bulk actions (publish, draft, delete)
- Status workflow (draft, pending, published, rejected)
- Auto-save for draft properties

### 4. Lookup Data Management
- Property types with unique slugs
- Amenities with icon support
- Locations with geographic data
- All data searchable and paginated

### 5. Media Integration
- WordPress Media Library integration for property images
- SVG icon support for amenities and locations
- Image validation (type, size, dimensions)
- Gallery management with drag-and-drop

### 6. Developer-Friendly
- Clean, well-documented codebase
- Multiple extension points
- AJAX action hooks for customization
- Database handler class for direct access

---

## Screenshots

### Main Features (Placeholder Descriptions)

1. **LEB Admin Menu** - Top-level WordPress admin menu with icon
2. **Database Management** - Table status and create/repair interface
3. **Types Management** - List, add, edit property types
4. **Amenities Management** - Create amenities with SVG icons
5. **Locations Management** - Manage destinations with icons
6. **Properties Dashboard** - Property listing with filters and bulk actions
7. **Add/Edit Property** - Comprehensive property form with gallery

---

## System Requirements

### Server Requirements
- **PHP Version:** 7.4 or higher (uses typed properties)
- **MySQL Version:** 5.0 or higher
- **WordPress Version:** 5.0 or higher

### WordPress Requirements
- Administrator access for setup
- Write access to database
- Media Library capability

### Browser Requirements
- Modern web browser (Chrome, Firefox, Safari, Edge)
- JavaScript enabled for AJAX operations

---

## Technology Stack

| Component | Technology |
|-----------|------------|
| Backend | PHP 7.4+ |
| Frontend (Admin) | Vanilla JavaScript |
| Styling | Plain CSS |
| Database | MySQL via $wpdb |
| UI Model | Custom wp-admin templates + AJAX |
| Media | WordPress Media Library |

### Architecture
- **Plugin Bootstrap:** `listing-engine-backend.php`
- **Database Layer:** `includes/db-schema.php`, `includes/class-db-handler.php`
- **Admin Interface:** `includes/admin-hooks.php`
- **Asset Management:** `includes/assets-loader.php`
- **Templates:** `templates/` directory
- **JavaScript:** `assets/js/` directory
- **Styles:** `assets/css/` directory
- **Components:** `components/` directory

---

## Installation Guide

### Step 1: Upload Plugin

1. Download the plugin zip file
2. Navigate to WordPress Admin > Plugins > Add New
3. Click "Upload Plugin" button
4. Choose the plugin zip file and click "Install Now"
5. Alternatively, upload via FTP to `/wp-content/plugins/`

### Step 2: Activate Plugin

1. Go to WordPress Admin > Plugins
2. Find "Listing Engine Backend" in the list
3. Click "Activate"

### Step 3: Initial Setup (Important)

After activation, the plugin does NOT automatically create database tables. You must manually create them:

1. Log in as Administrator
2. Navigate to **LEB > Database**
3. Click "Create / Repair" for each required table:
   - Types Table
   - Amenities Table
   - Locations Table
   - Property Table
   - Images Table
   - Block Dates Table

---

## Getting Started

### Recommended Setup Order

1. **Database** - Create all required tables first
2. **Types** - Add property types (Apartment, Villa, Cabin, etc.)
3. **Amenities** - Define amenities (WiFi, Pool, Parking, etc.)
4. **Locations** - Add destinations (Dubai, Goa, New York, etc.)
5. **Properties** - Start creating property listings

### Quick Start Checklist

- [ ] Activate plugin
- [ ] Create database tables
- [ ] Add at least one property type
- [ ] Add at least one amenity
- [ ] Add at least one location
- [ ] Create your first property

---

## Admin Modules

### 1. Types Module
**Purpose:** Manage property type categories

**Features:**
- Paginated list view with search
- Add/Edit type form with name and slug
- Auto-slug generation from name
- Duplicate slug prevention
- Bulk delete capability

**Location:** LEB > Types

### 2. Database Module
**Purpose:** Manage plugin database tables

**Features:**
- View status of all plugin tables
- Create new tables
- Repair existing tables
- Table status indicators

**Location:** LEB > Database

### 3. Amenities Module
**Purpose:** Define property amenities and features

**Features:**
- Amenity list with search and pagination
- Icon selection via WordPress Media Library
- Icon validation (SVG/WEBP, 24x24px, max 1MB)
- Bulk operations
- Name and icon management

**Location:** LEB > Amenities

### 4. Locations Module
**Purpose:** Manage destinations and regions

**Features:**
- Location list with search
- Add/Edit with name and unique slug
- Icon support via Media Library
- Slug auto-generation
- Duplicate prevention

**Location:** LEB > Locations

### 5. Properties Module
**Purpose:** Main property listing management

**Features:**
- Dashboard with status tabs (All, Draft, Pending, Published, Rejected)
- Live search functionality
- Bulk actions (Publish, Draft, Delete)
- Property duplication
- Add/Edit property form with:
  - Title and description
  - Property type selection
  - Location selection
  - Multiple amenity selection
  - Address and pricing
  - Guest capacity, bedrooms, beds, bathrooms
  - Image gallery (5-10 images required)
  - Blocked dates calendar
- Auto-save for drafts

**Location:** LEB > Properties

---

## Database Schema

### Table: `{prefix}ls_types`
Stores property type categories.

| Column | Type | Description |
|--------|------|-------------|
| id | bigint unsigned | Primary key, auto-increment |
| name | varchar(255) | Type display name |
| slug | varchar(255) | Unique URL-friendly identifier |
| updated_at | datetime | Last modification timestamp |

### Table: `{prefix}ls_amenities`
Stores available amenities.

| Column | Type | Description |
|--------|------|-------------|
| id | bigint unsigned | Primary key |
| name | varchar(255) | Amenity name |
| svg_path | varchar(2048) | Icon data (JSON with path + attachment ID) |
| updated_at | datetime | Last update |

### Table: `{prefix}ls_location`
Stores destinations and locations.

| Column | Type | Description |
|--------|------|-------------|
| id | bigint unsigned | Primary key |
| name | varchar(255) | Location name |
| slug | varchar(255) | Unique slug |
| svg_path | varchar(2048) | Icon JSON data |
| updated_at | datetime | Last update |

### Table: `{prefix}ls_property`
Core property listing table.

| Column | Type | Description |
|--------|------|-------------|
| id | bigint unsigned | Primary key |
| host_id | bigint unsigned | WordPress user ID of creator |
| title | varchar(255) | Property title |
| location | longtext | Location reference |
| address | longtext | Full address |
| amenities | longtext | Amenity IDs |
| type | varchar(255) | Property type |
| guests | int | Guest capacity |
| bedroom | int | Number of bedrooms |
| bed | int | Number of beds |
| bathroom | int | Number of bathrooms |
| description | longtext | Property description |
| price | bigint | Price per night |
| status | varchar(50) | draft/pending/published/rejected |
| updated_at | datetime | Last update |

### Table: `{prefix}ls_img`
Stores property gallery images (JSON format).

| Column | Type | Description |
|--------|------|-------------|
| id | bigint unsigned | Primary key |
| property_id | bigint unsigned | Related property |
| image | text | Full gallery JSON |

### Table: `{prefix}ls_block_date`
Stores blocked/unavailable dates.

| Column | Type | Description |
|--------|------|-------------|
| id | bigint unsigned | Primary key |
| property_id | bigint unsigned | Related property |
| dates | longtext | Blocked dates JSON |
| created_at | datetime | Creation timestamp |

---

## How It Works

### Data Flow

1. **User Action:** Admin performs action in wp-admin interface
2. **JavaScript:** AJAX call sent to admin-ajax.php
3. **PHP Handler:** Corresponding AJAX handler processes request
4. **Database Handler:** LEB_Database_Handler performs CRUD operation
5. **Database:** Data stored in custom MySQL tables
6. **Response:** JSON response returned to frontend
7. **UI Update:** JavaScript updates interface with result

### Property Creation Workflow

1. Admin opens Properties > Add New
2. Form loads lookup data (types, locations, amenities) via AJAX
3. Admin fills in property details
4. Admin selects images from Media Library (5-10 required)
5. Admin sets blocked dates using calendar
6. Form validates required fields
7. AJAX sends data to server
8. Database Handler creates:
   - Main property record
   - Gallery JSON record
   - Blocked dates JSON record
9. Success notification displayed

### Duplication Feature

When duplicating a property:
- Main property data is cloned
- Title gets " - Copy" suffix
- Status always resets to "draft"
- Gallery and blocked dates are also duplicated

---

## For Developers

### Understanding the Codebase

Key files to understand the plugin:

1. **listing-engine-backend.php**
   - Plugin entry point
   - Defines constants
   - Loads dependencies
   - Handles activation/deactivation

2. **includes/admin-hooks.php**
   - Menu registration
   - Page render callbacks
   - All AJAX handlers
   - SVG compatibility hooks

3. **includes/class-db-handler.php**
   - Central CRUD operations
   - Database table management
   - Data retrieval methods

4. **includes/db-schema.php**
   - Table creation SQL
   - Default data definitions
   - Table status checker

5. **includes/assets-loader.php**
   - Conditional CSS/JS loading
   - AJAX configuration
   - Asset path management

### Working with the Plugin

#### Adding a New Data Module

Follow this pattern:
1. Add schema function to `db-schema.php`
2. Add handler methods to `class-db-handler.php`
3. Add menu and AJAX hooks to `admin-hooks.php`
4. Create page template in `templates/`
5. Add JavaScript and CSS in `assets/`
6. Register assets in `assets-loader.php`

#### Database Handler Usage

```php
// Get database handler instance
$handler = new LEB_Database_Handler();

// Create a new type
$handler->create_type('Villa', 'villa');

// Get all amenities
$handler->get_amenities('', 1, 10);

// Update property
$handler->update_listing($property_id, $data);
```

#### AJAX Actions

All AJAX actions require:
- Capability: `manage_options`
- Nonce: `leb_nonce`

Example AJAX call:
```javascript
jQuery.ajax({
    url: ajaxurl,
    type: 'POST',
    data: {
        action: 'leb_get_types',
        nonce: leb_vars.nonce,
        search: '',
        page: 1
    },
    success: function(response) {
        console.log(response.data);
    }
});
```

### Available AJAX Actions

**Types:**
- `leb_get_types` - List types
- `leb_create_type` - Create type
- `leb_update_type` - Update type
- `leb_get_type` - Get single type
- `leb_delete_type` - Delete type
- `leb_bulk_delete_types` - Bulk delete

**Database:**
- `leb_db_status` - Get table status
- `leb_db_create_repair` - Create/repair table

**Amenities:**
- `leb_amen_get_amenities` - List amenities
- `leb_amen_create_amenity` - Create
- `leb_amen_update_amenity` - Update
- `leb_amen_get_amenity` - Get single
- `leb_amen_delete_amenity` - Delete
- `leb_amen_bulk_delete_amenities` - Bulk delete

**Locations:**
- `leb_loc_get_locations` - List
- `leb_loc_create_location` - Create
- `leb_loc_update_location` - Update
- `leb_loc_get_location` - Get single
- `leb_loc_delete_location` - Delete
- `leb_loc_bulk_delete_locations` - Bulk delete

**Properties:**
- `leb_listing_get_listings` - List properties
- `leb_listing_get_listing` - Get single
- `leb_listing_create_listing` - Create
- `leb_listing_update_listing` - Update
- `leb_listing_delete_listing` - Delete
- `leb_listing_bulk_delete` - Bulk delete
- `leb_listing_bulk_status` - Bulk status update
- `leb_listing_get_amenities_all` - Get all amenities
- `leb_listing_get_locations_all` - Get all locations
- `leb_listing_get_types_all` - Get all types
- `leb_listing_duplicate` - Duplicate property

---

## Extension Points

### Filters

- `leb_default_type_rows` - Filter default type entries for seeding

### Classes

- `LEB_Database_Handler` - Reusable class for CRUD and schema operations

### Template Customization

The best places to extend functionality:
- `templates/` - Add new admin UI pages
- `assets/js/` - Add new client-side interactions
- `assets-loader.php` - Register new module assets
- `admin-hooks.php` - Add new admin pages or AJAX handlers

---

## Security

### Implemented Security Measures

1. **Capability Checks**
   - Every admin page verifies `manage_options` capability

2. **Nonce Verification**
   - All AJAX requests verify `leb_nonce`

3. **Input Sanitization**
   - `sanitize_text_field()` for text fields
   - `sanitize_title()` for slugs
   - `esc_url_raw()` for URLs
   - `absint()` for integers
   - `wp_kses_post()` for HTML content

4. **Database Security**
   - Queries use `$wpdb->prepare()` where applicable
   - Safe database operations

5. **SVG Security**
   - Aggressive SVG compatibility for admin display
   - SVG metadata generation skipped to avoid processing failures

---

## Troubleshooting

### Tables Missing After Activation

**Issue:** Database tables not created after plugin activation.

**Solution:** This is expected. Tables must be manually created:
1. Go to LEB > Database
2. Click "Create / Repair" for each table

### SVG Uploads Failing

**Check:**
- Logged in as administrator
- File is SVG or SVGZ format
- Icon dimensions are 24x24px

### Amenity/Location Icon Not Displaying

**Check:**
- Stored SVG path contains valid path
- Media Library attachment still exists
- Icon is exactly 24x24px

### Property Creation Fails

**Check:**
- At least 5 images selected
- Images are JPEG, WEBP, or AVIF
- Each image ≤ 1MB
- Type, location, address, price, and title are present
- Custom tables exist

### Bulk Actions Not Working

**Check:**
- Logged in as administrator
- Nonce loaded correctly
- Check browser console for errors

---

## Changelog

### Version 2.5.8
- Current version
- Full CRUD operations for properties
- AJAX-powered admin interface
- Custom database tables
- Media Library integration
- Property duplication
- Bulk actions
- Blocked dates management

---

## Support & Contact

### Developer Information

**Plugin Developer:** Art-Tech Fuzion

**Company Website:** https://arttechfuzion.com

**Plugin URI:** https://arttechfuzion.com

### Support

For technical support, feature requests, or bug reports:

1. Visit our website: https://arttechfuzion.com
2. Contact through the website support channels
3. Report issues directly

### Custom Development

We also offer custom development services:
- Custom feature additions
- Integration with third-party systems
- Frontend development
- Theme integration

Contact us through our website for custom development inquiries.

---

## License

**License:** GPL-2.0-or-later

**License URI:** https://www.gnu.org/licenses/gpl-2.0.html

This plugin is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 2 of the License, or any later version.

This plugin is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

---

## Credits

Developed by **Art-Tech Fuzion**

Built with:
- WordPress
- PHP 7.4+
- MySQL
- Vanilla JavaScript

---

*Last Updated: May 2026*