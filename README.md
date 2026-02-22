# BestCar Commercial — Odoo Module

A custom Odoo module for the complete commercial management of a car dealership.
Developed as a final project during an Odoo training course.

**Authors:** Farid, Lorenzo, Jean-Marc  
**Version:** 0.1  
**License:** LGPL-3  
**Odoo Compatibility:** 15.0+

---

## 📋 Overview

`bestcar_commercial` covers the full lifecycle of a vehicle in a dealership:
from purchase and workshop reconditioning, through sale and payment, all the way to delivery.
Vehicle status transitions are automated by hooking into standard Odoo business flows
(purchase orders, sales orders, invoices, stock transfers, payments).

---

## ✨ Features

- **Vehicle catalog** — Each vehicle is modeled as an Odoo product, extended with technical
-   fields (VIN, license plate, engine, dimensions, emissions, mileage, etc.)
-   - **Automated status tracking** — Vehicle status updates automatically throughout the business flow
    - - **Workshop project automation** — Confirming a purchase order auto-creates a reconditioning
      -   project with predefined stages and tasks (Inspection, Repair, Maintenance, Cleaning)
      -   - **Trade-in management** — Marking a vehicle as trade-in automatically generates a mirrored
          -   product with a negative price for seamless inclusion in sale orders
          -   - **Stock time tracking** — Computed field tracking days between arrival and sale
              - - **Vehicle sheet (PDF report)** — Printable A4 vehicle sheet generated via QWeb
                - - **Role-based access** — Four permission groups: Technician, Workshop Manager, Salesman, Administrator
                 
                  - ---

                  ## 🔄 Vehicle Status Flow

                  ```
                  Added → Waiting Arrival → Reconditioning → For Sale → Reserved
                  → Payment → Waiting Technical Inspection → Waiting Delivery → Delivered
                  ```

                  ---

                  ## 🗂️ Module Structure

                  ```
                  bestcar_commercial/
                  ├── controllers/
                  ├── data/               # Preloaded brands, models, departments
                  ├── models/             # All business logic
                  │   ├── product_template.py     # Core vehicle model
                  │   ├── purchase_order.py       # Purchase flow + project creation
                  │   ├── sale_order.py           # Sale flow
                  │   ├── stock_picking.py        # Arrival & delivery tracking
                  │   ├── account_move.py         # Invoice & payment status updates
                  │   ├── vehicle_brand.py
                  │   ├── vehicle_model.py
                  │   └── vehicle_type.py
                  ├── reports/            # QWeb PDF vehicle sheet
                  ├── security/           # Groups and ACL
                  ├── views/              # All XML views and menus
                  └── wizard/             # Payment register extension
                  ```

                  ---

                  ## ⚙️ Dependencies

                  ```python
                  ['base', 'product', 'sale_management', 'project', 'hr', 'purchase', 'stock', 'account']
                  ```

                  ---

                  ## 🚀 Installation

                  1. Copy the `bestcar_commercial` folder into your Odoo `addons` directory.
                  2. 2. Restart the Odoo server.
                     3. 3. Activate developer mode in Odoo settings.
                        4. 4. Go to **Apps**, click **Update Apps List**, search for `bestcar_commercial` and install it.
                          
                           5. ---
                          
                           6. ## 👥 User Roles
                          
                           7. | Role | Description |
                           8. |---|---|
                           9. | Technician | Base read access |
                           10. | Workshop Manager | Manages reconditioning projects and tasks |
                           11. | Salesman | Manages vehicle sales |
                           12. | Administrator | Full access — inherits all roles |
                          
                           13. ---
                          
                           14. ## 📄 License
                          
                           15. This module is distributed under the [LGPL-3 License](https://www.gnu.org/licenses/lgpl-3.0.html).
