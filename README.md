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
1.table_id ( table being used )
2.username ( who is using )
3.hours (3 hours or 6 hours)
4.start_time ( when started )
5.cost ( total price )
6.end_time_str ( when ended )

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
(Purpose)           (Color Name)    (Hex Code)        (Usage)
Window Background     BG_DARK        #1a1a2e        Main window bg
Card Background       BG_CARD        #16213e        Dialogs, frames
Panel Background      BG_PANEL       #0f3460        Headers, footer
Primary Accent        ACCENT         #e94560        Main buttons
Secondary Accent      ACCENT2        #f5a623        Gold highlights
Available Status      GREEN          #2ecc71        Available tables
Available Hover       GREEN_DARK     #27ae60        Hover on green
In-Use Status         TABLE_BUSY     #e74c3c        Busy tables
Hover Effect          TABLE_HOVER    #f39c12        Hover on tables
Neutral/Disabled      GREY_MID       #4a4a6a        Disabled elements
Primary Text          TEXT_LIGHT     #eaeaea        Main text
Secondary Text        TEXT_DIM       #8888aa        Dim text

2. fonts
    Element             Font          Size    Weight   
Page Title            Segoe UI         22      Bold  
 Dialog/Window Title  Segoe UI         14      Bold   
 Body Text            Segoe UI         11     Normal 
 Button Text          Segoe UI         11      Bold  
  Small               Segoe UI          9     Normal 
Technical             Courier New      11      Bold

## Configuration Documentation

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
