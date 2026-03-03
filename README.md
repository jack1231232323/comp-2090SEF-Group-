# comp-2090SEF-Group-
# Mahjong Table Management System

A desktop application for managing mahjong table bookings and player accounts. Built with “Python” and “Tkinter”, this system provides table session tracking, account balance management, and session control.

## Code Analysis
**class** 
(it is an account. It stores the name, secret password, and how much money user have. The check_password() method verifies they entered the correct password.)
-class User:
1. username (name of the player)
2. password_hash (secret password, encrypted)
3. balance (money in account)
4. check_password() (verify if password matches)

**Session**
(one mahjong table session. It records which table, who is using it, how many hours they booked, when they started, and automatically calculates when they'll finish and how much it costs)
-class Session:
1. table_id ( table being used )
2. username ( who is using )
3. hours (3 hours or 6 hours)
4. start_time ( when started )
5. cost ( total price )
6. end_time_str ( when ended )

**Repository**
(it can store the user and session, creat account , save data when starts and save it to the file)
Repository (The Storage Manager):
1. Load data from file on startup
2. Add user (register)
3. Check user login
4. open table session
5.  Close table session
6.  Save all data to file

## Features

**User Management**
- register new account with username and password
- password using SHA-256 hashing

**Balance Management** 
- Top-up account balance with quick-amount buttons and custom amounts
- Real-time balance updates
- Validation for positive amounts only


**Session Tracking**
- Monitor active sessions and remaining balances


**Table Management**
- Support for up to 4 concurrent mahjong sessions
- Visual indicators for available and in-use tables
- Open and close tables with cost calculation
- Choose from preset durations (3 hours = $30, 6 hours = $60)

**Dashboard**
- Overview of all table (Available / Using)
- User information display (username and balance)
- Value-Added Shortcut

**Owner Authentication** 
- Only table owners can close their sessions

**Cost Transparency** 
- Instant cost calculation with balance validation

**Responsive Updates** 
- Real-time UI refresh after any action

## Architecture mapping (color, font,setting)
1. Data Layer
   DATA_FILE = "mahjong_data.json"
RATE_PER_HOUR = 10
TABLE_IDS = ["0001", "0002", "0003", "0004"]
# Colors
# Fonts
# Helper function

2.Models Layer (data structure)
# class User
# class session

3.Persistence Layer (storage )
# class Repository

4.UI Helper Layer(styling , reusable)
# _style_entry
# _round_btn
# _on
# _off
# _label

5.UI Window Layer (user interface)
# AuthWindow
# TopUpDialog
# TableCard
# OpenTableDialog
# Dashboard

## Design system
1. color
   <table border="1" cellpadding="8" cellspacing="0">
  <thead>
    <tr>
      <th>Purpose</th>
      <th>Color Name</th>
      <th>Usage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Window Background</td>
      <td>BG_DARK</td>
      <td>Main window bg</td>
    </tr>
    <tr>
      <td>Card Background</td>
      <td>BG_CARD</td>
      <td>Dialogs, frames</td>
    </tr>
    <tr>
      <td>Panel Background</td>
      <td>BG_PANEL</td>
      <td>Headers, footer</td>
    </tr>
    <tr>
      <td>Primary Accent</td>
      <td>ACCENT</td>
      <td>Main buttons</td>
    </tr>
    <tr>
      <td>Secondary Accent</td>
      <td>ACCENT2</td>
      <td>Gold highlights</td>
    </tr>
    <tr>
      <td>Available Status</td>
      <td>GREEN</td>
      <td>Available tables</td>
    </tr>
    <tr>
      <td>Available Hover</td>
      <td>GREEN_DARK</td>
      <td>Hover on green</td>
    </tr>
    <tr>
      <td>In-Use Status</td>
      <td>TABLE_BUSY</td>
      <td>Busy tables</td>
    </tr>
    <tr>
      <td>Hover Effect</td>
      <td>TABLE_HOVER</td>
      <td>Hover on tables</td>
    </tr>
    <tr>
      <td>Neutral/Disabled</td>
      <td>GREY_MID</td>
      <td>Disabled elements</td>
    </tr>
    <tr>
      <td>Primary Text</td>
      <td>TEXT_LIGHT</td>
      <td>Main text</td>
    </tr>
    <tr>
      <td>Secondary Text</td>
      <td>TEXT_DIM</td>
      <td>Dim text</td>
    </tr>
  </tbody>
</table>

2. fonts
<table border="1" cellpadding="8" cellspacing="0">
  <thead>
    <tr>
      <th>Element</th>
      <th>Font</th>
      <th>Size</th>
      <th>Weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Page Title</td>
      <td>Segoe UI</td>
      <td>22</td>
      <td>Bold</td>
    </tr>
    <tr>
      <td>Dialog/Window Title</td>
      <td>Segoe UI</td>
      <td>14</td>
      <td>Bold</td>
    </tr>
    <tr>
      <td>Body Text</td>
      <td>Segoe UI</td>
      <td>11</td>
      <td>Normal</td>
    </tr>
    <tr>
      <td>Button Text</td>
      <td>Segoe UI</td>
      <td>11</td>
      <td>Bold</td>
    </tr>
    <tr>
      <td>Small</td>
      <td>Segoe UI</td>
      <td>9</td>
      <td>Normal</td>
    </tr>
    <tr>
      <td>Technical</td>
      <td>Courier New</td>
      <td>11</td>
      <td>Bold</td>
    </tr>
  </tbody>
</table>

## Configuration Documentation

**Configuration 1**
- variable name: DATA_FILE
- type: String
- Default Value:	"mahjong_data.json"
- Format: JSON
- Location in project: mahjong_system.py
- Who uses it: class repository

**configuration 2**
- Variable Name:	RATE_PER_HOUR
- Type:	Integer
- Default Value:	10
- Currency: Yuan (¥)
- Unit:	Per hour
- Purpose:	Base pricing for table sessions
- Who uses it:	Repository.open_table(), OpenTableDialog

**configuration 3**
- Variable Name:	TABLE_IDS
- Type:	List of Strings
- Default Value:	["0001", "0002", "0003", "0004"]
- Format:	4-digit strings
- Count:	4 tables
- Purpose:	All available table identifiers
- Who uses it:Dashboard (creates TableCard for each)

## User guide
**register**
1. user see two pages (login and register) and the management system
2. user click 'register'
3. enter name and password
4. confirm password
5. click register button
6. account requirment:
- Username at least 2 characters
- Password at least 4 characters
- Passwords match
- Username doesn't exist
7. user created successful and save to file
8. switch to the page of the management system
**login**
1. open the "Login" tab
2. Type your username
3. Type your password
4. Click "Login" button
5. successful:
- AuthWindow closes
- Dashboard appears
- You see your username in header
6. error:
- Red error message shows
- Check username and password
**Top-up**
1. User clicks "Top-Up" button in header
2. TopUpDialog window opens
3. Shows current balance
4. User can choose:
- Click quick amount button (¥30, ¥50, ¥100, ¥200)
- Type custom amount
5. System requirement:
- Amount is a number
- Amount is greater than 0
6. System adds to balance
7. System saves to file
8. Success message shown
**book table**
1.user will see 4 table
2.user can open table with green status
3.OpenTableDialog window opens
4.Shows table ID and current balance
5.User selects duration:
- 3 hours = ¥30
- 6 hours = ¥60
6. Cost displays and updates
7. User clicks "Confirm"
8. System validates:
- Table not already in use
- not all tables in use
- User has enough balance
9. System deducts cost from balance
10. System creates Session record
11. System saves to file
12. Dialog closes
13. Dashboard refreshes
14. Table now shows "In Use"
**show the table details**
1. User looks at a table card
2. If table is "In Use":
3. Card shows:
- Username of who booked it
- Duration booked
- Total cost
- Estimated end time
**close the table**
You're on Dashboard
1. Look at your table marked with red border if owned by you)
2. See "Close Table" button (red)
3. Click "Close Table" button
4. Confirmation dialog appears:
- Title: "Confirm Close"
- Message: "Are you sure you want to close Table 000X?"
- Buttons: Yes/No
5. Click "Yes" to close
If successful:
- Success dialog shows: "Table 0001 closed"
- Dashboard refreshes
- Table card updates:
- Badge: "Available" (green)
- Button: "Open Table" (green)
If you click "No":
- Nothing changes
## Installation
**Language**
-  Python 3.8+

**GUI Framework**
- Tkinter

**Library**
- 'tkinter' (UI)
- 'ttk' (styled widgets)
- 'hashlib' (password hashing)
- 'dataclasses' (domain models)
- 'json' and 'os' (data persistence)
- 'datetime' (session timing) 

**No external dependencies (uses only standard library)**
- Clone the repository:
   ```bash
   git clone https://github.com/yourusername/mahjong-table-management.git cd mahjong-table-management
python mahjong_system.py
