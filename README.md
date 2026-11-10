# 🚨 ResQCommand

> **A browser-based Emergency Response Command Center for reporting,
> tracking, and managing emergency incidents with GPS-assisted location
> capture and an interactive incident map.**

![Platform](https://img.shields.io/badge/platform-Web%20Browser-blue.svg)
![Frontend](https://img.shields.io/badge/frontend-HTML%20%7C%20CSS%20%7C%20JavaScript-orange.svg)
![Map](https://img.shields.io/badge/maps-Leaflet%20%7C%20OpenStreetMap-green.svg)
![Storage](https://img.shields.io/badge/storage-Browser%20LocalStorage-lightgrey.svg)

------------------------------------------------------------------------

## 📌 Problem Statement

During emergencies such as medical incidents, fires, road accidents, and
rescue situations, people need a simple way to report what has happened
and where help is required. If incident details are scattered across
calls or messages, response teams may find it difficult to view all
reported incidents, identify critical cases, and track their progress.

**ResQCommand** provides a single browser-based dashboard where a
reporter can submit an emergency report, capture their current location
using the device's GPS permission, and view reported incidents on an
incident dashboard and map. The dashboard also provides basic incident
status management.

The current project is a front-end prototype. It stores incident records
in the browser's local storage and does not include a connected
emergency-services backend or automatic dispatch system.

------------------------------------------------------------------------

## 🚀 Features

  --------------------------------------------------------------------------------
  Feature         Subsystem      Implementation      Output         Status
  --------------- -------------- ------------------- -------------- --------------
  **Emergency     Incident       Collects reporter   A new incident Implemented
  Report Form**   Reporting      name, contact       record.        
                                 number, emergency                  
                                 type, severity,                    
                                 location, and                      
                                 description through                
                                 a form.                            

  **GPS Location  Location       Uses the browser    Latitude and   Implemented
  Capture**       Assistance     Geolocation API     longitude      
                                 after the user      entered into   
                                 selects **Use My    the location   
                                 Location** and      field.         
                                 grants permission.                 

  **Incident      Map View       Uses Leaflet with   Interactive    Implemented
  Map**                          OpenStreetMap tiles map with       
                                 and displays        incident       
                                 markers for         markers.       
                                 incidents with                     
                                 captured                           
                                 coordinates.                       

  **Incident      Incident       Displays incident   Central list   Implemented
  Dashboard**     Management     type, severity,     of submitted   
                                 location,           incidents.     
                                 description,                       
                                 reporter, time, and                
                                 status.                            

  **Incident      Dashboard      Filters the         Matching       Implemented
  Search**                       incident list using incident       
                                 location, type, and records.       
                                 severity text.                     

  **Status        Incident       Allows the status   Updated        Implemented
  Tracking**      Management     of an incident to   incident       
                                 be changed among    status.        
                                 Pending,                           
                                 Responding, and                    
                                 Resolved.                          

  **Incident      Incident       Provides a delete   Selected       Implemented
  Deletion**      Management     action with a       incident       
                                 confirmation        removed from   
                                 prompt.             the local      
                                                     list.          

  **Summary       Dashboard      Counts total,       Summary cards  Implemented
  Statistics**    Analytics      critical,           at the top of  
                                 responding, and     the dashboard. 
                                 resolved incidents.                

  **Local Data    Browser        Saves incident      Records remain Implemented
  Persistence**   Storage        records in          available in   
                                 `localStorage`      the same       
                                 under the key       browser        
                                 `resq_incidents`.   storage.       
  --------------------------------------------------------------------------------

------------------------------------------------------------------------

## 🏗️ Tech Stack

### Frontend

  -----------------------------------------------------------------------
  Component               Technology              Role
  ----------------------- ----------------------- -----------------------
  **Structure**           HTML5                   Defines the reporting
                                                  form, statistics, map
                                                  area, and incident
                                                  dashboard.

  **Styling**             CSS3                    Provides the dark
                                                  command-center
                                                  interface, cards,
                                                  responsive layout, and
                                                  form styling.

  **Application Logic**   JavaScript              Handles form
                                                  submission, incident
                                                  records, searching,
                                                  status updates,
                                                  deletion, and
                                                  statistics.
  -----------------------------------------------------------------------

### Maps & Location

  -----------------------------------------------------------------------
  Component               Technology / API        Role
  ----------------------- ----------------------- -----------------------
  **Interactive Map**     Leaflet 1.9.4           Displays the map and
                                                  incident markers.

  **Map Tiles**           OpenStreetMap           Supplies the map tile
                                                  layer.

  **Location Capture**    Browser Geolocation API Requests permission and
                                                  reads the device's
                                                  current coordinates.
  -----------------------------------------------------------------------

### Data Storage

  -----------------------------------------------------------------------
  Component               Technology              Role
  ----------------------- ----------------------- -----------------------
  **Incident Storage**    Browser `localStorage`  Stores the incident
                                                  array locally in the
                                                  browser.

  **Record Format**       JavaScript objects      Represents incident
                          serialized as JSON      details, status,
                                                  coordinates, and
                                                  submission time.
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 📂 Project Structure

The supplied project is a single-page HTML application:

``` text
ResQCommand/
└── index.html
    ├── HTML
    │   ├── Header
    │   ├── Summary statistics
    │   ├── Emergency report form
    │   ├── Incident map
    │   └── Incident dashboard
    ├── CSS
    │   ├── Dark theme and layout
    │   ├── Cards and form controls
    │   └── Responsive grid
    └── JavaScript
        ├── Incident data and local storage
        ├── GPS location capture
        ├── Form submission
        ├── Status update and deletion
        ├── Search and dashboard rendering
        └── Leaflet map markers
```

------------------------------------------------------------------------

## ⚙️ Installation & Setup

### Prerequisites

-   A modern web browser.
-   An internet connection to load the Leaflet library and OpenStreetMap
    map tiles from the external services referenced in the HTML.
-   Location permission enabled in the browser if GPS capture is to be
    used.
-   A local web server is recommended when testing browser geolocation.
    Browser security rules may restrict geolocation on pages opened
    directly from the file system.

### Step 1: Get the Project

Save the supplied HTML file as `index.html` inside a project folder
named `ResQCommand`.

``` text
ResQCommand/
└── index.html
```

### Step 2: Run the Application

Open the project using a local development server, or use a browser
environment that supports the required APIs.

For example, if Python is installed, open a terminal in the project
folder and run:

``` bash
python -m http.server 8000
```

Then open:

``` text
http://localhost:8000
```

### Step 3: Allow Location Access

1.  Select **Use My Location**.
2.  Allow the browser to access the device location when prompted.
3.  After successful capture, the coordinates are placed in the incident
    location field.
4.  Submit the incident form to save the report with the captured
    coordinates.

If location permission is denied or the browser does not support
geolocation, enter the incident location manually.

### Step 4: Submit and Manage an Incident

1.  Enter the reporter's name and contact number.
2.  Select the emergency type and severity.
3.  Enter the incident location and description.
4.  Select **Submit Incident**.
5.  Find the new report in the Incident Dashboard.
6.  Change its status when its progress changes, or delete it if
    required.

------------------------------------------------------------------------

## 🧠 How It Works

ResQCommand follows a simple browser-side workflow:

``` text
                 RESQCOMMAND WORKFLOW

        Reporter opens the web application
                       |
                       v
             Enters emergency details
                       |
             +---------+---------+
             |                   |
             v                   v
      Enters location       Uses GPS button
      manually              and grants access
             |                   |
             +---------+---------+
                       |
                       v
              Submits incident form
                       |
                       v
             JavaScript creates record
                       |
                       v
           Saves record in localStorage
                       |
             +---------+---------+
             |                   |
             v                   v
      Updates dashboard      Adds map marker
      and statistics         when coordinates
                             are available
             |
             v
       Search / update status /
          delete incident
```

### 1. Emergency Reporting

The reporting form collects the following information:

-   Reporter name
-   Contact number
-   Emergency type: Medical, Fire, Accident, Rescue, or Other
-   Severity: Critical, High, Medium, or Low
-   Incident location
-   Incident description

When the form is submitted, JavaScript creates an incident object
containing a unique timestamp-based ID, the submitted details, a default
`Pending` status, available GPS coordinates, and the submission time.

### 2. GPS Location Capture

The **Use My Location** button calls the browser's Geolocation API. If
the user grants permission, the application reads latitude and longitude
and places the coordinate pair in the location input. The coordinates
are also retained with the incident record so that the map can display a
marker.

GPS capture is optional. A report can be submitted with a manually
entered location, but it will not have a coordinate-based map marker
unless coordinates are available.

### 3. Local Storage

The application reads previously saved records from the browser's
`localStorage` using the key `resq_incidents`. When an incident is
submitted, updated, or deleted, the application saves the incident array
as JSON and refreshes the dashboard.

Because this is browser-local storage, the records are not automatically
shared between different devices, browsers, or users.

### 4. Dashboard and Status Tracking

The dashboard renders the saved incidents and provides a search field.
Search checks the incident's location, emergency type, and severity.

Each incident has a status selector with three available states:

-   **Pending** --- the report has been submitted.
-   **Responding** --- the incident is marked as being responded to.
-   **Resolved** --- the incident is marked as resolved.

The summary cards calculate the total number of incidents and the number
marked Critical, Responding, and Resolved.

### 5. Map Visualization

The map is initialized using Leaflet and centered on Chennai.
OpenStreetMap supplies the map tiles. When the dashboard is rendered,
existing markers are cleared and recreated for incidents that contain
GPS coordinates. Selecting a marker displays the incident type and
severity.

------------------------------------------------------------------------

## 📈 Scalability & Extension Possibilities

The current implementation is a single-browser prototype. The following
are possible future development directions; they are not implemented in
the supplied HTML file:

1.  **Shared Incident Database:** Replace browser-only storage with a
    server-side database so authorized users can access the same
    incident records.
2.  **User Authentication:** Add separate reporter, responder, and
    administrator accounts with role-based permissions.
3.  **Real-Time Updates:** Add a backend and WebSocket or another
    real-time communication mechanism to distribute incident updates to
    connected dashboards.
4.  **Responder Assignment:** Add a workflow for assigning incidents to
    available response teams and tracking assignment progress.
5.  **Notification System:** Add notifications for newly reported
    critical incidents and status changes.
6.  **Improved Location Search:** Add address lookup or geocoding so
    manually entered locations can be converted into map coordinates.
7.  **Incident History:** Maintain an audit trail of status changes and
    other incident actions.

These extensions would require additional application services, data
storage, security controls, and testing.

------------------------------------------------------------------------

## 💡 Feasibility

-   **Simple to run:** The supplied application is a single HTML file
    and does not require a separate backend to demonstrate its current
    features.
-   **Accessible interface:** It can be used in a modern browser on
    desktop or mobile-sized screens.
-   **Low setup requirements:** The project uses browser technologies
    and externally loaded map resources.
-   **Easy to demonstrate:** A user can submit sample incidents, search
    the list, update statuses, and view available GPS markers.
-   **Prototype limitations:** Local storage is browser-specific and is
    not suitable by itself for coordinated emergency response across
    multiple users or devices.

------------------------------------------------------------------------

## 🌟 Novelty & Practical Value

ResQCommand brings several basic emergency-reporting functions together
in one interface:

-   A structured form for recording emergency details.
-   GPS-assisted entry of the reporter's current coordinates.
-   A map view for incidents with coordinate data.
-   A searchable incident list.
-   Simple severity and response-status summaries.

Its practical value as a prototype is the combination of reporting,
location display, and incident tracking in one lightweight browser
application. A production emergency-response service would need reliable
backend infrastructure, verified responder workflows, secure handling of
personal information, and integration with authorized emergency
services.

------------------------------------------------------------------------

## ⚠️ Limitations & Operational Disclaimer

ResQCommand, as supplied, is a demonstration prototype and **is not an
official emergency-services system**.

-   **No automatic dispatch:** Submitting an incident does not contact
    police, fire services, ambulance services, or rescue teams.
-   **No shared server:** Incident records are stored in the current
    browser's local storage and are not automatically transmitted to
    response personnel.
-   **No guaranteed location accuracy:** GPS availability and accuracy
    depend on the device, browser, permissions, and surrounding
    conditions.
-   **External map dependency:** Map display requires access to the
    external Leaflet library and OpenStreetMap tile service.
-   **Personal information:** Reporter names and contact numbers are
    stored in browser storage. Do not enter real emergency or personal
    information into an unapproved demonstration environment.
-   **Human verification:** Incident details and status values are
    user-entered and should not be treated as independently verified.

For a real emergency, contact the appropriate official emergency service
directly. Do not rely on this prototype as the sole method of requesting
help.

------------------------------------------------------------------------

## 📜 License

No license information was included in the supplied project file. Add a
license before distributing or reusing the project.

------------------------------------------------------------------------

## 🧩 Author & Team

Add the project team's names, roles, institution, and repository link
here.
