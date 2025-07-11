# app.garlip.com-releases
# Garlip Changelog

All notable changes to the Garlip application will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---
## [0.1.1] - 2025-07-11 - Google Drive Integration

This release adds the functionality to store creative content on the users own Google Drive folder.

### Added
-   **Menu Icons:** Created icon to view collateral stored on Google drive.
-   **Dashboard:** Copyrights stored on the Google drive have a clickable icon next to the datatable record.
-   **Google Sync:** Sync index in Google drive ensures app has the source of truth.
-   **Blockchain:**
    -   Bulk batch blockchain writes where it is a bit slow onchain.
    -   Blockchain proof json includes copyright meta and file type.

## [0.1.0] - 2025-07-10 - Initial Release

This is the initial beta release of the Garlip application, establishing the core infrastructure and features for copyright registration and web scraping.

### Added

-   **User Authentication:** Secure user sign-up and login using Google and Microsoft accounts.
-   **SSO Integration:** Single Sign-On flow established with session management and logging.
-   **Stripe Subscription Foundation:**
    -   Integrated Stripe library.
    -   Created database tables to store customer and subscription data.
    -   Implemented Stripe Checkout flow for new subscriptions.
    -   Added a Stripe Webhook endpoint to handle subscription status changes (`active`, `canceled`, etc.).
-   **Copyright Dashboard:**
    -   Main user interface for uploading files and registering copyrights.
    -   Features file hashing (SHA-256) on the client-side.
    -   Displays a paginated and searchable table of all registered copyrights.
-   **Dynamic Navigation Menu:**
    -   Centralized, server-driven menu system.
    -   Menu items are fetched from an API based on user role.
    -   Admins see additional links for management pages.
    -   Desktop view uses a clean, icon-based menu with tooltips.
    -   Mobile view uses a traditional responsive burger menu.
-   **Admin User Management:**
    -   Secure page for administrators to view all registered users.
    -   Admins can manually toggle a user's `isLive` (paid) status.
-   **Web Scraper Service:**
    -   A background worker that periodically checks for new content from registered sources.
    -   A robust process that fetches content, checks for changes via hashing, and stores new content as copyrights.
    -   Added table for managing URLs to be scraped.
-   **Admin Bot Management - robots.txt:**
    -   UI for viewing scrape collateral and managing scrape sources.
    -   Admins can add, update, and delete sources.
    -   Includes a "Force Run" button to manually trigger the scraping process for all active sources.
-   **Custom Error Pages:** Added user-friendly pages for 404 (Not Found), 403 (Forbidden), and 500 (Server Error).

### Changed

-   Refactored application startup to enforce clean, extensionless URLs (e.g., `/my-account` instead of `/my-account.html`).
-   Improved database connection management in background services using `IServiceScopeFactory` to prevent leaks and errors.

### Fixed

-   Resolved numerous bugs related to Dependency Injection, routing conflicts, and database constraint violations.
-   Corrected UI display issues where menu items were duplicated or had conflicting event listeners.
-   Hardened API endpoints against common errors (e.g., duplicate entries, null data).
