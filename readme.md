# WiFi Billing System with M-pesa Integration

An MVP setup for Hotspot Billing using PHPNuxBill and FreeRADIUS

## Quick Start

1. Clone this repository
```bash
git clone --recursive git@github.com:reduzersolutions/radius-billing-system.git
```
2. Create a src folder at the root directory and clone this repository inside the src folder

```bash
git clone git@github.com:reduzersolutions/phpnuxbill.git .

```


3. Create a .env file
```bash
touch .env
```
4. Copy contents of the .env.example into the newly created .env
```bash
cp .env.example .env
```
5. Edit the env file with correct configurations
```
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=billing
DB_USERNAME=your_username
DB_PASSWORD=your_secure_password

```

5. Start the containers
```bash
docker-compose up -d
```

## Initial Setup

### 1. PHPNuxBill Installation
1. Open your browser and navigate to `http://localhost`
2. Follow the PHPNuxBill installation wizard
3. Once logged in, go to:
    - Settings → General Settings → FreeRADIUS
    - Enable RADIUS integration
    - Save changes

### 2. NAS Configuration
1. Navigate to Settings → General Settings → FreeRADIUS
2. Turn on Radius
3. Go to RADIUS → RADIUS NAS
4. Add your router details:
    - Name: [Your Router Name]
    - IP Address: [Router IP]
    - Secret Key: [Your Secret] // We will use this when setting up radius on Mikrotik

### 3. MikroTik Hotspot Setup
For detailed MikroTik configuration, watch this tutorial: [How to create a Hotspot with Radius Server Authentication](https://www.youtube.com/watch?v=bH_6MS9T_n4)

**Important**: Do not use MikroTik's UserManager as PHPNuxBill will handle user management.

## M-pesa Integration

The system includes M-pesa integration for automated payments. Configure your M-pesa credentials in PHPNuxBill's payment settings.

**NB**: You can use Ngrok for testing M-pesa integration on your local machine.

## System Components

- **PHPNuxBill**: Billing and user management
- **FreeRADIUS**: Authentication server
- **MySQL**: Database backend
- **Nginx**: Web server


##  Additional Resources

- [PHPNuxBill Documentation](https://github.com/hotspotbilling/phpnuxbill/wiki)
- [FreeRADIUS Documentation](https://wiki.freeradius.org/guide/HOWTO)
- [MikroTik Documentation](https://help.mikrotik.com/docs/spaces/ROS/pages/328151/First+Time+Configuration)


---

## Note to Developers

This is the most basic setup I could put together. I basically combined a bunch of opensource projects to just make it work - PHPNuxBill and FreeRADIUS. Not perfect, but it works.

I really need your help in making this better. My goal is to make it super easy to deploy and run in minimal time. 


- Create scripts that auto-configure MikroTik and PHPNuxBill with all the necessary credentials
- Enhance security
- Make customer onboarding and payments smoother

If you choose to use this project, please make internet accessible to your community. Even if you can only offer 1Mbps, do it - but make sure EVERYONE can afford it. Why? Because internet access literally turned my life around. I want to give others the same opportunity.



    
