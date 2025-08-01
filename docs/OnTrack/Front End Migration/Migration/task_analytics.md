# OnTrack Component Review

## Team Member Name

### Pasindu Fernando

### Student ID : 
s224263102

## Component Name
Analytics Configuration (virtual page views)

### Files in this Component
analytics.coffee (to be removed)

## Description

The analytics.coffee file was previously responsible for configuring Google Analytics tracking in the AngularJS version of the application. Its key functionality included disabling automatic route change tracking by setting ``` $analyticsProvider.virtualPageviews(false) ```, preventing virtual pageviews from being recorded.

## Why Removal is Required

It is no longer functional due to the migration to Angular 17.

All analytics functionality has been migrated to Google Analytics 4 (GA4), which is fully managed through gtag.js in index.html.

Virtual pageviews and event tracking are now handled explicitly using Angular’s Router and manual event tracking with gtag().



## Screenshots
before commenting analytics.coffee file and depenency in config.coffee

![before commenting analytics.coffee file and depenency in config.coffee](https://github.com/user-attachments/assets/6e10e0c3-0962-4cad-9988-b8d08d54b4a6)



## Component Migration Plan:

1. Remove the File:analytics.coffee


2. Clean Up Dependencies:
    Remove doubtfire.config.analytics from config.coffee.
    Delete any references to angulartics or $analyticsProvider in doubtfire-angularjs.module.ts.

