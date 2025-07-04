# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.5.1] - 2025-06-06

### Fixed

- Issues with Prisma Merge script after working with `zod-prisma`

## [0.5.0] - 2025-06-03

### Added
- Added email tool (`npx rwsdk-tools email`) for setting up email functionality with Resend
  - Implemented automatic installation of the Resend package
  - Added environment variable configuration for Resend API key
  - Created email client setup in src/app/lib/email.ts
  - Added optional integration with React Email for creating email templates
  - Added comprehensive documentation for the email tool
- Added windsurf tool (`npx rwsdk-tools windsurf`) for setting up code quality checks and workflows
  - Created default rules for common code quality issues
  - Added workflow templates for pre-commit and PR checks
  - Implemented non-destructive installation that preserves existing configurations
  - Added comprehensive documentation for the windsurf tool
- Added addon tools for managing RedwoodSDK addons:
  - Added addonGenerate tool (`npx rwsdk-tools addon generate`) for generating addon configuration files
    - Automatically analyzes addon content to generate addon.jsonc files
    - Detects required packages, environment variables, and dependencies
    - Identifies CSS files, routes, and ShadCN components used in the addon
    - Adds an `addon:generate` script to package.json
  - Added addonInstall tool (`npx rwsdk-tools addon install`) for installing RedwoodSDK addons
    - Supports installation from local directories or GitHub repositories
    - Handles all aspects of addon installation including dependencies, environment variables, and routes
    - Provides flexible options for source and destination directories
    - Adds an `addon:install` script to package.json

### Changed
- Modified the seedToSql tool to place files in the `src/scripts` directory instead of the root `scripts` directory
- Updated the seedToSql tool to place generated SQL files in the `src/scripts` directory
- Improved consistency with other tools that use the `src/scripts` directory

## [0.4.1] - 2025-06-03

### Added
- Updated the shadcn/ui setting to turn React Server Components on

## [0.4.0] - 2025-06-02

### Added
- Added colored output to the CLI for improved readability and user experience
- Implemented color-coding: green for success messages, cyan for process messages, yellow for warnings, and red for errors
- Added bold formatting for important headings like "Next steps" and "Usage"
- Added Prisma schema merger tool (`npx rwsdk-tools merge`):
  - Automatically merges multiple Prisma schema files into a single schema.prisma file
  - Backs up existing schema.prisma file to schema.prisma.bak before overwriting
  - Includes backup file content in the merge process
  - Handles model merging with field deduplication
  - Supports schema files from multiple directories
  - Preserves model additions from commented sections
- Enhanced route generator to support external route files with multiple import patterns:
  - Direct variable references in prefix calls: `prefix("/user", userRoutes)`
  - Spread syntax for route arrays: `...userRoutes`
  - Improved path resolution for imported route files
- Fixed component generator to properly respect command-line flags, allowing non-interactive component creation:
  - Added support for `--file` and `--folder` structure flags
  - Added support for `--stories`, `--no-stories`, `--tests`, and `--no-tests` flags
  - Improved flag parsing to properly bypass interactive prompts when flags are provided
- Enhanced seedToSql tool with improved compatibility and error handling:
  - Added enhanced regex patterns to better match different seed file formats
  - Added fallback parsing methods for complex data structures
  - Added deduplication function to remove duplicate SQL statements
  - Added support for seed files using the latest RedwoodSDK imports
  - Added auto-detection of the default seed file (src/scripts/seed.ts) when no input file is specified
  - Fixed handling of `db.user.create()` operations
  - Fixed handling of DELETE statements in User table
  - Improved error handling to suppress unnecessary warnings
  - Improved console output to be more user-friendly

### Changed
- Updated ShadCN setup tool to be compatible with the latest version of RedwoodSDK
- Removed unnecessary configuration for tsconfig.json and vite.config.mts files
- Streamlined the setup process for ShadCN UI integration
- Fixed Tailwind setup tool to preserve existing styles.css content instead of overwriting it
- Enhanced ShadCN setup to intelligently inject styles into existing styles.css files rather than overwriting them

## [0.3.0] - 2025-05-20

### Added
- Added Seed to SQL converter tool (`npx rwsdk-tools seedtosql`)
- Created a dependency-free script that converts Redwood seed files to raw SQL
- Added support for various Prisma operations including `createMany`, `create`, and `$executeRawUnsafe`
- Implemented handling for nested relations and complex data structures
- Added comprehensive documentation for the seedToSql tool

## [0.2.0] - 2025-05-15

### Added
- Added shadcn UI setup tool (`npx rwsdk-tools shadcn`)
- Created a pre-configured components.json file for RedwoodSDK projects
- Added utilities to automatically install shadcn dependencies
- Implemented proper Document.tsx file updates for style imports
- Added comprehensive documentation for the shadcn tool

### Fixed
- Fixed issue with Tailwind setup not properly adding style imports to Document.tsx
- Improved error handling in configuration file updates
- Enhanced robustness of tsconfig.json and vite.config.ts modifications

## [0.1.0] - 2025-05-12

### Added
- Initial CLI framework for installing utility tools in RedwoodSDK projects
- Added routes generator tool (`npx rwsdk-tools routes`)
- Added component generator tool with Plop integration (`npx rwsdk-tools component`)
- Added Tailwind CSS setup tool (`npx rwsdk-tools tailwind`)
- Implemented automatic dependency installation
- Created comprehensive documentation for all tools
