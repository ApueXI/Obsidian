---
Created: 2025-06-12T15:22
---
```Python
flask install migrate
from flask_migrate import Migrate

with app.app_context():
        db.create_all()
        add_data()
        

def add_data():
    from .models import Product
    try:
        if Product.query.count() == 0:  # Only add if the table is empty
            """
            parts = [
                {"product_name": "AMD Ryzen 5 7600X", "price": 11427.99, "stock": 10, "manufacturer": "AMD", "category": "CPU"},
                {"product_name": "Intel Core i5-13600K", "price": 19500.00, "stock": 15, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "AMD Ryzen 9 5900X", "price": 13359.00, "stock": 5, "manufacturer": "AMD", "category": "CPU"},
                {"product_name": "Intel Core i9-11900K", "price": 31399.00, "stock": 8, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "Intel Core i5-11400F", "price": 10000.00, "stock": 20, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "NVIDIA GeForce RTX 3090", "price": 220000.00, "stock": 5, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "AMD Radeon RX 6800 XT", "price": 148000.00, "stock": 8, "manufacturer": "AMD", "category": "GPU"},
                {"product_name": "NVIDIA GeForce GTX 1660 Ti", "price": 20000.00, "stock": 12, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "AMD Radeon RX 5700 XT", "price": 22000.00, "stock": 10, "manufacturer": "AMD", "category": "GPU"},
                {"product_name": "NVIDIA GeForce RTX 3070", "price": 65000.00, "stock": 6, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "MSI MAG B550 TOMAHAWK", "price": 7500.00, "stock": 14, "manufacturer": "MSI", "category": "MOBO"},
                {"product_name": "ASUS ROG Strix Z590-E", "price": 13500.00, "stock": 7, "manufacturer": "ASUS", "category": "MOBO"},
                {"product_name": "Gigabyte B450 AORUS M", "price": 4300.00, "stock": 16, "manufacturer": "Gigabyte", "category": "MOBO"},
                {"product_name": "ASRock Z390 Phantom Gaming 4", "price": 5900.00, "stock": 11, "manufacturer": "ASRock", "category": "MOBO"},
                {"product_name": "MSI MPG Z490 GAMING EDGE WIFI", "price": 9200.00, "stock": 9, "manufacturer": "MSI", "category": "MOBO"},
            ]
            """
            many_parts = [
                # CPUs
                {"product_name": "AMD Ryzen 5 7600X", "price": 11427.99, "stock": 10, "manufacturer": "AMD", "category": "CPU"},
                {"product_name": "Intel Core i5-13600K", "price": 19500.00, "stock": 15, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "AMD Ryzen 9 5900X", "price": 13359.00, "stock": 5, "manufacturer": "AMD", "category": "CPU"},
                {"product_name": "Intel Core i9-11900K", "price": 31399.00, "stock": 8, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "Intel Core i5-11400F", "price": 10000.00, "stock": 20, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "AMD Ryzen 7 5800X3D", "price": 15000.00, "stock": 10, "manufacturer": "AMD", "category": "CPU"},
                {"product_name": "Intel Core i7-14700K", "price": 27000.00, "stock": 12, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "AMD Ryzen 7 7700X", "price": 16000.00, "stock": 7, "manufacturer": "AMD", "category": "CPU"},
                {"product_name": "Intel Core i3-12100F", "price": 6500.00, "stock": 18, "manufacturer": "Intel", "category": "CPU"},
                {"product_name": "AMD Ryzen 5 5600G", "price": 7500.00, "stock": 13, "manufacturer": "AMD", "category": "CPU"},

                # GPUs
                {"product_name": "NVIDIA GeForce RTX 3090", "price": 220000.00, "stock": 5, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "AMD Radeon RX 6800 XT", "price": 148000.00, "stock": 8, "manufacturer": "AMD", "category": "GPU"},
                {"product_name": "NVIDIA GeForce GTX 1660 Ti", "price": 20000.00, "stock": 12, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "AMD Radeon RX 5700 XT", "price": 22000.00, "stock": 10, "manufacturer": "AMD", "category": "GPU"},
                {"product_name": "NVIDIA GeForce RTX 3070", "price": 65000.00, "stock": 6, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "NVIDIA GeForce RTX 4060", "price": 27000.00, "stock": 15, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "AMD Radeon RX 7600", "price": 23000.00, "stock": 10, "manufacturer": "AMD", "category": "GPU"},
                {"product_name": "NVIDIA GeForce RTX 4080", "price": 98000.00, "stock": 7, "manufacturer": "NVIDIA", "category": "GPU"},
                {"product_name": "AMD Radeon RX 7900 XTX", "price": 96000.00, "stock": 5, "manufacturer": "AMD", "category": "GPU"},
                {"product_name": "NVIDIA GeForce RTX 4070 Ti", "price": 74000.00, "stock": 9, "manufacturer": "NVIDIA", "category": "GPU"},

                # Motherboards
                {"product_name": "MSI MAG B550 TOMAHAWK", "price": 7500.00, "stock": 14, "manufacturer": "MSI", "category": "MOBO"},
                {"product_name": "ASUS ROG Strix Z590-E", "price": 13500.00, "stock": 7, "manufacturer": "ASUS", "category": "MOBO"},
                {"product_name": "Gigabyte B450 AORUS M", "price": 4300.00, "stock": 16, "manufacturer": "Gigabyte", "category": "MOBO"},
                {"product_name": "ASRock Z390 Phantom Gaming 4", "price": 5900.00, "stock": 11, "manufacturer": "ASRock", "category": "MOBO"},
                {"product_name": "MSI MPG Z490 GAMING EDGE WIFI", "price": 9200.00, "stock": 9, "manufacturer": "MSI", "category": "MOBO"},
                {"product_name": "ASUS TUF Gaming B550-PLUS", "price": 7400.00, "stock": 13, "manufacturer": "ASUS", "category": "MOBO"},
                {"product_name": "Gigabyte X570 AORUS Elite", "price": 9800.00, "stock": 10, "manufacturer": "Gigabyte", "category": "MOBO"},
                {"product_name": "ASRock B550M Steel Legend", "price": 6800.00, "stock": 12, "manufacturer": "ASRock", "category": "MOBO"},
                {"product_name": "MSI PRO Z790-A WiFi", "price": 11900.00, "stock": 8, "manufacturer": "MSI", "category": "MOBO"},
                {"product_name": "ASUS Prime B660M-A", "price": 7200.00, "stock": 14, "manufacturer": "ASUS", "category": "MOBO"},

                # RAM
                {"product_name": "Corsair Vengeance LPX 16GB DDR4 3200MHz", "price": 2800.00, "stock": 25, "manufacturer": "Corsair", "category": "RAM"},
                {"product_name": "G.Skill Trident Z RGB 16GB DDR4 3600MHz", "price": 4000.00, "stock": 20, "manufacturer": "G.Skill", "category": "RAM"},
                {"product_name": "Kingston Fury Beast 16GB DDR4 3200MHz", "price": 2900.00, "stock": 18, "manufacturer": "Kingston", "category": "RAM"},
                {"product_name": "TeamGroup T-Force Delta RGB 16GB DDR5 6000MHz", "price": 5800.00, "stock": 10, "manufacturer": "TeamGroup", "category": "RAM"},
                {"product_name": "Corsair Dominator Platinum 32GB DDR5 5600MHz", "price": 8800.00, "stock": 12, "manufacturer": "Corsair", "category": "RAM"},
                {"product_name": "ADATA XPG Spectrix D60G 16GB DDR4", "price": 3300.00, "stock": 15, "manufacturer": "ADATA", "category": "RAM"},
                {"product_name": "Patriot Viper Steel 16GB DDR4 3600MHz", "price": 3100.00, "stock": 14, "manufacturer": "Patriot", "category": "RAM"},
                {"product_name": "Crucial Ballistix 16GB DDR4 3200MHz", "price": 2700.00, "stock": 20, "manufacturer": "Crucial", "category": "RAM"},
                {"product_name": "Lexar ARES RGB 32GB DDR4", "price": 6400.00, "stock": 9, "manufacturer": "Lexar", "category": "RAM"},
                {"product_name": "Silicon Power 16GB DDR4 2666MHz", "price": 2500.00, "stock": 22, "manufacturer": "Silicon Power", "category": "RAM"},

                # Storage
                {"product_name": "Samsung 970 EVO Plus 1TB NVMe", "price": 4900.00, "stock": 15, "manufacturer": "Samsung", "category": "Storage"},
                {"product_name": "WD Blue SN570 1TB NVMe", "price": 4200.00, "stock": 18, "manufacturer": "Western Digital", "category": "Storage"},
                {"product_name": "Crucial MX500 1TB SATA SSD", "price": 3900.00, "stock": 20, "manufacturer": "Crucial", "category": "Storage"},
                {"product_name": "Seagate Barracuda 2TB HDD", "price": 3200.00, "stock": 25, "manufacturer": "Seagate", "category": "Storage"},
                {"product_name": "Kingston A2000 1TB NVMe", "price": 4500.00, "stock": 12, "manufacturer": "Kingston", "category": "Storage"},
                {"product_name": "ADATA XPG SX8200 Pro 1TB", "price": 4600.00, "stock": 10, "manufacturer": "ADATA", "category": "Storage"},
                {"product_name": "Samsung 980 PRO 2TB NVMe", "price": 9900.00, "stock": 6, "manufacturer": "Samsung", "category": "Storage"},
                {"product_name": "Toshiba P300 1TB HDD", "price": 2300.00, "stock": 20, "manufacturer": "Toshiba", "category": "Storage"},
                {"product_name": "WD Black SN850X 1TB NVMe", "price": 7200.00, "stock": 9, "manufacturer": "Western Digital", "category": "Storage"},
                {"product_name": "Silicon Power A60 1TB NVMe", "price": 4100.00, "stock": 14, "manufacturer": "Silicon Power", "category": "Storage"},

                # PSUs
                {"product_name": "Corsair RM750x 750W 80+ Gold", "price": 5200.00, "stock": 10, "manufacturer": "Corsair", "category": "PSU"},
                {"product_name": "Seasonic Focus GX-750 80+ Gold", "price": 5400.00, "stock": 7, "manufacturer": "Seasonic", "category": "PSU"},
                {"product_name": "EVGA 600 BR 80+ Bronze", "price": 2900.00, "stock": 15, "manufacturer": "EVGA", "category": "PSU"},
                {"product_name": "Cooler Master MWE Gold 750 V2", "price": 4800.00, "stock": 12, "manufacturer": "Cooler Master", "category": "PSU"},
                {"product_name": "Thermaltake Smart 500W 80+", "price": 2600.00, "stock": 20, "manufacturer": "Thermaltake", "category": "PSU"},
                {"product_name": "Antec Earthwatts Gold Pro 750W", "price": 5100.00, "stock": 8, "manufacturer": "Antec", "category": "PSU"},
                {"product_name": "Gigabyte P650B 650W 80+ Bronze", "price": 3100.00, "stock": 10, "manufacturer": "Gigabyte", "category": "PSU"},
                {"product_name": "NZXT C850 850W 80+ Gold", "price": 5800.00, "stock": 6, "manufacturer": "NZXT", "category": "PSU"},
                {"product_name": "ASUS ROG STRIX 750W 80+ Gold", "price": 6000.00, "stock": 5, "manufacturer": "ASUS", "category": "PSU"},
                {"product_name": "SilverStone Strider Essential 600W", "price": 2800.00, "stock": 13, "manufacturer": "SilverStone", "category": "PSU"},

                # Peripherals
                {"product_name": "Logitech G502 Hero Mouse", "price": 2800.00, "stock": 20, "manufacturer": "Logitech", "category": "Peripheral"},
                {"product_name": "Razer BlackWidow V3 Mechanical Keyboard", "price": 5200.00, "stock": 12, "manufacturer": "Razer", "category": "Peripheral"},
                {"product_name": "Corsair HS50 PRO Stereo Headset", "price": 3200.00, "stock": 10, "manufacturer": "Corsair", "category": "Peripheral"},
                {"product_name": "Redragon K552 Kumara RGB Keyboard", "price": 2100.00, "stock": 18, "manufacturer": "Redragon", "category": "Peripheral"},
                {"product_name": "SteelSeries Rival 5 Gaming Mouse", "price": 3500.00, "stock": 11, "manufacturer": "SteelSeries", "category": "Peripheral"},
                {"product_name": "Logitech C920 HD Webcam", "price": 4200.00, "stock": 7, "manufacturer": "Logitech", "category": "Peripheral"},
                {"product_name": "HyperX Cloud II Gaming Headset", "price": 4700.00, "stock": 8, "manufacturer": "HyperX", "category": "Peripheral"},
                {"product_name": "ASUS ROG Strix Scope Keyboard", "price": 5900.00, "stock": 5, "manufacturer": "ASUS", "category": "Peripheral"},
                {"product_name": "Razer Basilisk V3 Mouse", "price": 3900.00, "stock": 9, "manufacturer": "Razer", "category": "Peripheral"},
                {"product_name": "A4Tech Bloody A70 Light Strike Mouse", "price": 1600.00, "stock": 25, "manufacturer": "A4Tech", "category": "Peripheral"}
            ]


            
            for part in many_parts:
                new_part = Product(
                    product_name=part["product_name"],
                    price=part["price"],
                    stock=part["stock"],
                    manufacturer=part["manufacturer"],
                    category=part["category"]
                    # date_created and date_updated will be automatically handled
                )
                db.session.add(new_part)

            db.session.commit()
            print("Data added successfully!")
        else:
            print("Data already exists in the database.")
    except Exception as e:
        print(f"Error adding data: {e}")
    finally:
        db.session.close()
```

```Python
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned

.\venv\Scripts\activate.ps1 or
venv\Scripts\activate

pip3 install virtualenv
virtualenv venv
pip install -r requirements.txt

python
import secrets
secrets.token_hex()

--------------------------


   with app.app_context():
        db.create_all()

    @app.teardown_appcontext
    def shutdown_session(exception=None):
        db.session.remove()

    return app

def create_database(app):
    if not path.exists('website/' + db_name):
        db.create_all(app=app)
        print('Created Database!')
```