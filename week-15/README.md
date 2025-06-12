<div align="center">

# LAPORAN PRAKTIKUM
## WORKSHOP ADMINISTRASI JARINGAN

**Projek 2 - Express API Container, Mysql Container & Power BI**

<img src="https://upload.wikimedia.org/wikipedia/id/4/44/Logo_PENS.png" alt="Logo PENS" width="200">

### **Informasi Praktikum**

**Dosen Pengampu**: Dr. Ferry Astika Saputra, S.T., M.Sc.  
**Mahasiswa**: Danur Isa Prabutama  
**NRP**: 3123500023  
**Kelas**: 2-D3 IT A  
**Kelompok**: 1  


**POLITEKNIK ELEKTRONIKA NEGERI SURABAYA**  
DEPARTEMEN TEKNIK INFORMATIKA DAN KOMPUTER  
PROGRAM STUDI TEKNIK INFORMATIKA  
**2025**

---

</div>

# **Daftar Isi**
- [Ringkasan Projek](#ringkasan-projek)
- [Analisis Sistem dan Arsitektur](#analisis-sistem-dan-arsitektur)
- [Teknologi dan Tech Stack](#teknologi-dan-tech-stack)
- [Implementasi dan Fitur Sistem](#implementasi-dan-fitur-sistem)
- [Struktur Proyek dan Organisasi Kode](#struktur-proyek-dan-organisasi-kode)
- [Database & API Configuration](#database--api-configuration)
- [Implementasi dan Testing](#implementasi-dan-testing)
- [Instalasi dan Konfigurasi](#instalasi-dan-konfigurasi)
- [API Endpoints Documentation](#api-endpoints-documentation)
- [Deployment](#deployment)
- [Testing & Business Intelligence](#testing--business-intelligence)
- [Kesimpulan](#kesimpulan)
- [Referensi dan Sumber](#referensi-dan-sumber)

---

## **Ringkasan Projek**

P2-OC-API adalah sistem REST API berbasis Node.js yang menyediakan akses terstruktur dan analitik mendalam terhadap database ClassicModels. Sistem ini terdiri dari 68 endpoint API yang terbagi dalam 7 kategori utama, dengan arsitektur 3-tier (presentation, application, data layer) yang jelas.

**Fitur Utama:**
- Backend: Node.js v18+ & Express.js v4.18.2
- Database: MySQL v8.0.33 (8 tabel, 3000+ records)
- Frontend: Web dashboard responsif (vanilla JS)
- Deployment: Docker Compose multi-container
- Performa: <500ms response time untuk sebagian besar endpoint
- Dokumentasi: API & user guide lengkap

**Tujuan Projek:**
- Mengimplementasikan REST API yang scalable dan maintainable
- Menyediakan interface analitik bisnis melalui dashboard interaktif
- Menerapkan best practices API modern dan dokumentasi
- Containerization (Docker) untuk deployment konsisten
- Query database kompleks untuk business intelligence
- Monitoring & health check untuk reliability

**Ruang Lingkup:**
- 68 endpoint REST API untuk analisis bisnis
- Web dashboard real-time
- 7 controller modules untuk entitas bisnis
- Advanced analytics (trend, BI)
- Containerization penuh (Docker)
- Database management (MySQL, pooling)
- Dokumentasi lengkap

**Manfaat Sistem:**
- Efisiensi operasional: akses data cepat & terstruktur
- Analisis bisnis: insight performa penjualan & customer
- Skalabilitas: arsitektur siap berkembang
- Maintainability: kode terorganisir & mudah dipelihara
- Portabilitas: deployment konsisten lintas environment

**Teknologi Kunci:**
- Node.js, Express.js, MySQL, Docker, EJS, CSS3, Vanilla JS, Font Awesome, Helmet, CORS, Morgan

**Arsitektur:**
- 3-tier (presentation, application, data)
- MVC, repository, singleton, factory, middleware, RESTful

**Keamanan & Performa:**
- Helmet.js, input validation, SQL injection prevention
- Connection pooling, async/await, modular code, error handling

**Testing & Deployment:**
- API testing (Postman), monitoring, health check
- Docker Compose, manual & production deployment


## **Analisis Sistem dan Arsitektur**

### **Analisis Kebutuhan Sistem**

#### **Kebutuhan Fungsional**
- **Data Access Layer**
  - Koneksi database MySQL dengan connection pooling
  - Query optimization untuk performa tinggi
  - Transaction support untuk data integrity

- **Business Logic Layer**
  - 68 endpoints API untuk berbagai analisis bisnis
  - Data aggregation dan statistical analysis
  - Stored procedures integration
  - Real-time data processing

- **Presentation Layer**
  - Web dashboard dengan interface yang responsif
  - API documentation yang interaktif
  - Real-time monitoring dashboard
  - Cross-platform compatibility

#### **Kebutuhan Non-Fungsional**
- **Performance**: Response time < 500ms untuk query sederhana
- **Scalability**: Dapat menangani 1000+ concurrent requests
- **Reliability**: Uptime minimal 99.5%
- **Security**: Input validation dan SQL injection prevention
- **Maintainability**: Modular code structure dengan dokumentasi lengkap

### **Arsitektur Sistem**

#### **Arsitektur Aplikasi**
Proyek ini menggunakan **3-Tier Architecture** dengan pemisahan yang jelas:

```
┌─────────────────────────────────────────┐
│           PRESENTATION LAYER            │
│  ┌─────────────────┐ ┌─────────────────┐│
│  │   Web Dashboard │ │   API Clients   ││
│  │   (HTML/CSS/JS) │ │   (Postman/etc) ││
│  └─────────────────┘ └─────────────────┘│
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│            APPLICATION LAYER            │
│  ┌─────────────────────────────────────┐│
│  │         Express.js Server           ││
│  │  ┌─────────────┐ ┌─────────────────┐││
│  │  │   Routes    │ │   Controllers   │││
│  │  │             │ │                 │││
│  │  │ customers   │ │ customersCtrl   │││
│  │  │ employees   │ │ employeesCtrl   │││
│  │  │ orders      │ │ ordersCtrl      │││
│  │  │ payments    │ │ paymentsCtrl    │││
│  │  │ products    │ │ productsCtrl    │││
│  │  │ offices     │ │ officesCtrl     │││
│  │  │ productlines│ │ productLinesCtrl│││
│  │  └─────────────┘ └─────────────────┘││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────┐
│             DATA LAYER                  │
│  ┌─────────────────────────────────────┐│
│  │          MySQL Database             ││
│  │                                     ││
│  │  ┌───────────┐ ┌───────────┐       ││
│  │  │customers  │ │employees  │       ││
│  │  └───────────┘ └───────────┘       ││
│  │  ┌───────────┐ ┌───────────┐       ││
│  │  │  orders   │ │ payments  │       ││
│  │  └───────────┘ └───────────┘       ││
│  │  ┌───────────┐ ┌───────────┐       ││
│  │  │ products  │ │  offices  │       ││
│  │  └───────────┘ └───────────┘       ││
│  │  ┌───────────┐                     ││
│  │  │productlines│                    ││
│  │  └───────────┘                     ││
│  └─────────────────────────────────────┘│
└─────────────────────────────────────────┘
```

### **Pola Arsitektur dan Design Patterns**
- **MVC (Model-View-Controller)**: Pemisahan logika bisnis, presentasi, dan kontrol
- **Repository Pattern**: Abstraksi akses data melalui layer database
- **Singleton Pattern**: Database connection pool management
- **Factory Pattern**: Controller dan route initialization
- **Middleware Pattern**: Request processing pipeline (CORS, authentication, logging)
- **RESTful Architecture**: Consistent API design dengan HTTP verbs yang tepat

### **Database Schema dan Relationships**

#### **Foreign Key Constraints**
- `customers.salesRepEmployeeNumber → employees.employeeNumber`
- `employees.reportsTo → employees.employeeNumber` (self-referencing)
- `employees.officeCode → offices.officeCode`
- `orders.customerNumber → customers.customerNumber`
- `orderdetails.orderNumber → orders.orderNumber`
- `orderdetails.productCode → products.productCode`
- `products.productLine → productlines.productLine`
- `payments.customerNumber → customers.customerNumber`

---

## **Teknologi dan Tech Stack**

### **Backend Technology Stack**

| **Kategori** | **Teknologi** | **Versi** | **Deskripsi** | **Justifikasi Pemilihan** |
|-------------|---------------|-----------|---------------|---------------------------|
| **Runtime Environment** | Node.js | 18+ | JavaScript runtime environment | Performa tinggi, ecosystem yang besar, async I/O |
| **Web Framework** | Express.js | 4.18.2 | Minimal web application framework | Lightweight, flexible, middleware support |
| **Database** | MySQL | 8.0 | Relational database management system | ACID compliance, mature, excellent performance |
| **Database Driver** | mysql2 | 3.9.7 | MySQL driver dengan Promise support | Connection pooling, prepared statements |
| **Environment Management** | dotenv | 16.4.5 | Environment variables management | Security, configuration flexibility |

### **Frontend Technology Stack**

| **Kategori** | **Teknologi** | **Versi** | **Deskripsi** | **Justifikasi Pemilihan** |
|-------------|---------------|-----------|---------------|---------------------------|
| **Template Engine** | EJS | 3.1.10 | Embedded JavaScript templates | Server-side rendering, dynamic content |
| **Styling** | CSS3 | - | Custom responsive design | Native performance, full control |
| **JavaScript** | Vanilla JS | ES6+ | Client-side interactivity | No dependencies, fast loading |
| **Icons** | Font Awesome | 6.0.0 | Icon library | Comprehensive icons, CDN availability |

### **DevOps & Infrastructure**

| **Kategori** | **Teknologi** | **Versi** | **Deskripsi** | **Keunggulan** |
|-------------|---------------|-----------|---------------|----------------|
| **Containerization** | Docker | Latest | Application containerization | Portability, consistency, isolation |
| **Orchestration** | Docker Compose | Latest | Multi-container management | Service dependency, networking |
| **Web Server** | Express Static | Built-in | Static file serving | Integrated, minimal configuration |
| **Security** | Helmet | 7.0.0 | Security headers middleware | XSS protection, content security |
| **CORS** | CORS | 2.8.5 | Cross-origin resource sharing | API accessibility, security |
| **Logging** | Morgan | 1.10.0 | HTTP request logger | Debugging, monitoring, analytics |

### **Development & Monitoring Tools**

| **Kategori** | **Teknologi** | **Deskripsi** | **Fungsi dalam Proyek** |
|-------------|---------------|---------------|-------------------------|
| **Package Manager** | npm | Node package manager | Dependency management, scripts |
| **API Testing** | Postman | API development and testing | Endpoint testing, documentation |
| **Database Client** | MySQL Workbench | Database administration | Schema design, query optimization |
| **Code Quality** | ESLint (recommended) | Static code analysis | Code consistency, error prevention |
| **Documentation** | JSDoc (recommended) | Code documentation | API documentation, maintainability |

### **Architecture Benefits**

#### **Teknologi Modern**
- **Node.js**: Single-threaded event loop untuk handling concurrent requests
- **Express.js**: Minimalist framework dengan ecosystem middleware yang besar
- **MySQL**: Battle-tested database dengan excellent performance untuk analytical queries

#### **Scalability Features**
- **Connection Pooling**: Efficient database connection management
- **Async/Await**: Non-blocking I/O operations
- **Modular Architecture**: Easy horizontal scaling

#### **Security Implementation**
- **Helmet.js**: Security headers (XSS, CSRF protection)
- **Input Validation**: Parameter sanitization
- **SQL Injection Prevention**: Prepared statements

---

## **Implementasi dan Fitur Sistem**

### **Struktur Kode dan Komponen**

#### **Controllers Layer (7 modules)**
Berisi business logic untuk setiap entitas dengan total **66+ methods**:

| **Controller** | **Methods** | **Fungsi Utama** | **Key Features** |
|---------------|-------------|------------------|------------------|
| **customersController.js** | 15+ methods | Customer management & analytics | Segmentasi pelanggan, credit analysis, geographic distribution |
| **employeesController.js** | 9+ methods | Employee management & hierarchy | Performance tracking, organizational structure |
| **ordersController.js** | 11+ methods | Order processing & analytics | Trend analysis, delivery tracking, status management |
| **paymentsController.js** | 9+ methods | Payment analytics | Revenue analysis, customer payment behavior |
| **productsController.js** | 12+ methods | Product management | Inventory analysis, vendor performance, customer preferences |
| **officesController.js** | 6+ methods | Office management | Geographic distribution, employee allocation |
| **productLinesController.js** | 4+ methods | Product category management | Category performance, product line analysis |

#### **Routes**
Mendefinisikan **68 API endpoints** dengan RESTful patterns:

| **Route File** | **Endpoints** | **HTTP Methods** | **Primary Functions** |
|---------------|---------------|------------------|--------------------|
| **customers.js** | 15 endpoints | GET | Customer CRUD, analytics, segmentation |
| **employees.js** | 9 endpoints | GET | Employee management, hierarchy analysis |
| **orders.js** | 11 endpoints | GET | Order tracking, trend analysis |
| **payments.js** | 10 endpoints | GET | Payment processing, revenue analytics |
| **products.js** | 13 endpoints | GET | Product management, inventory analysis |
| **offices.js** | 6 endpoints | GET | Office management, geographic analysis |
| **productlines.js** | 4 endpoints | GET | Category management, performance analysis |

### **API Features dan Capabilities**

#### **Advanced Analytics Features**
- **Customer Intelligence**
  - Customer segmentation by credit limit, geography, purchase behavior
  - Sales representative performance tracking
  - Customer lifetime value analysis
  - Geographic distribution analysis

- **Sales & Revenue Analytics**
  - Monthly/yearly revenue trends
  - Order fulfillment analysis
  - Payment pattern analysis
  - Product performance metrics

- **Operational Intelligence**
  - Employee hierarchy and reporting structure
  - Office productivity analysis
  - Inventory management and stock levels
  - Vendor performance tracking

#### **Business Intelligence Queries**
- **Window Functions**: Running totals, ranking, percentile calculations
- **Complex JOINs**: Multi-table relationships for comprehensive analysis
- **Aggregation Functions**: Statistical analysis and summary reports
- **Stored Procedures**: Optimized database procedures for complex operations

#### **Technical Features**
- **Connection Pooling**: Efficient database connection management (max 10 connections)
- **Error Handling**: Comprehensive error management dengan detailed logging
- **Input Validation**: Request parameter validation dan sanitization
- **Response Formatting**: Consistent JSON response format
- **Health Monitoring**: Database dan application health checks
- **CORS Support**: Cross-origin request handling untuk API accessibility

### **Web Dashboard Features**

#### **Interactive Dashboard Components**
- **Real-time Data Visualization**
  - Dynamic tables dengan sorting dan filtering
  - Statistical cards untuk key metrics
  - Interactive navigation antar sections

- **Responsive Design**
  - Mobile-first approach
  - Cross-browser compatibility
  - Modern CSS Grid dan Flexbox layout

- **User Experience Features**
  - Loading states dan error handling
  - Refresh buttons untuk real-time updates
  - Intuitive navigation dengan icons

#### **Dashboard Sections**
- **Customers**: Total customers, geographic analysis, credit analysis
- **Employees**: Employee directory, hierarchy view, performance metrics
- **Orders**: Order trends, status tracking, delivery analysis
- **Payments**: Revenue analysis, payment patterns, top customers
- **Products**: Inventory status, product performance, vendor analysis
- **Offices**: Office locations, employee distribution

### **Performance Optimizations**

#### **Database Optimizations**
- **Prepared Statements**: SQL injection prevention dan performance
- **Connection Pooling**: Resource management dan scalability
- **Index Optimization**: Database indexes untuk query performance
- **Query Optimization**: Efficient SQL queries untuk complex analytics

#### **Application Optimizations**
- **Async/Await**: Non-blocking I/O operations
- **Error Handling**: Graceful error recovery
- **Caching Strategy**: Static asset caching
- **Compression**: Response compression untuk faster loading

---

## **Struktur Proyek dan Organisasi Kode**

### **Project Directory Structure**
```
p2-oc-api/                          # Root directory
├── controllers/                    # Business Logic Layer (66+ methods)
│   ├── customersController.js      # Customer analytics (15 methods)
│   ├── employeesController.js      # Employee management (9 methods)
│   ├── officesController.js        # Office operations (6 methods)
│   ├── ordersController.js         # Order processing (11 methods)
│   ├── paymentsController.js       # Payment analytics (9 methods)
│   ├── productLinesController.js   # Category management (4 methods)
│   └── productsController.js       # Product management (12 methods)
├── routes/                         # API Routing Layer (68 endpoints)
│   ├── customers.js                # 15 customer endpoints
│   ├── employees.js                # 9 employee endpoints
│   ├── offices.js                  # 6 office endpoints
│   ├── orders.js                   # 11 order endpoints
│   ├── payments.js                 # 10 payment endpoints
│   ├── productlines.js             # 4 product line endpoints
│   └── products.js                 # 13 product endpoints
├── public/                         # Frontend Static Files
│   ├── index.html                  # Main dashboard (329 lines)
│   ├── docs.html                   # API documentation page
│   ├── styles.css                  # Responsive styling (500+ lines)
│   └── script.js                   # Client-side JavaScript (400+ lines)
├── mysql_data/                     # Auto-generated MySQL data
│   ├── classicmodels/              # Database files
│   │   ├── customers.ibd           # Customer data
│   │   ├── employees.ibd           # Employee data
│   │   ├── orders.ibd              # Order data
│   │   ├── payments.ibd            # Payment data
│   │   ├── products.ibd            # Product data
│   │   ├── productlines.ibd        # Product line data
│   │   └── offices.ibd             # Office data
│   └── [system_files]              # MySQL system files
├── Configuration Files
│   ├── server.js                   # Main application entry (130 lines)
│   ├── db.js                       # Database configuration (38 lines)
│   ├── package.json                # Dependencies & scripts
│   ├── docker-compose.yml          # Multi-container setup
│   ├── Dockerfile                  # Application container
│   └── .env.example                # Environment template
├── Database Files
│   ├── data.sql                    # Initial database (7930 lines)
│   └── query.sql                   # Sample queries (335 lines)
└── Documentation
    └── README.md                   # Comprehensive documentation
```

### **Detailed Component Analysis**

#### **Controllers Layer Deep Dive**

**Customer Controller** (`customersController.js`):
- `getAllCustomers()` - Basic customer listing
- `getTotalCustomers()` - Customer count statistics
- `getCustomersWithFullName()` - Formatted customer names
- `getHighestCustomersByCountry()` - Geographic analysis
- `getHighestCustomersByCity()` - City-based segmentation
- `getHighestCustomersByState()` - State-level analysis
- `getCustomersWithoutState()` - Data quality analysis
- `getCustomersByCreditLimit()` - Credit-based filtering
- `getHighCreditCustomers()` - High-value customer identification
- `getHighestCreditCustomer()` - Top credit limit customer
- `getLowestCreditCustomer()` - Lowest credit limit customer
- `getCustomersWithoutSalesRep()` - Unassigned customers
- `getCustomerCreditStatus()` - Credit categorization
- `getCustomersByContactName()` - Contact-based search
- `getCustomerDetails()` - Stored procedure integration

**Employee Controller** (`employeesController.js`):
- `getAllEmployees()` - Employee directory
- `getTotalEmployees()` - Headcount statistics
- `getCustomersPerSalesRep()` - Performance metrics
- `getEmployeeForCustomers()` - Customer assignments
- `getEmployeeHierarchy()` - Organizational structure
- `getExecutives()` - Leadership identification
- `getEmployeesByTitle()` - Role-based filtering
- `getEmployeeById()` - Individual employee lookup
- `getEmployeesByOffice()` - Location-based grouping

#### **Routes Layer Implementation**

**Endpoint Distribution by Category**:
```javascript
Customers:     15 endpoints (22% of total)
Products:      13 endpoints (19% of total)  
Orders:        11 endpoints (16% of total)
Payments:      10 endpoints (15% of total)
Employees:      9 endpoints (13% of total)
Offices:        6 endpoints (9% of total)
Product Lines:  4 endpoints (6% of total)
Total:         68 endpoints (100%)
```

**HTTP Methods Distribution**:
- GET: 68 endpoints (100%) - Read-only analytics focus
- POST/PUT/DELETE: 0 endpoints - Analysis-only system

#### **Database Layer Architecture**

**Connection Configuration**:
```javascript
Database Pool Settings:
- connectionLimit: 10
- queueLimit: 0
- acquireTimeout: 60000
- timeout: 60000
- reconnect: true
```


### **Database & API Configuration**

#### **Database Configuration Details**

##### **Database Schema Specifications**
```sql
Database: classicmodels
Character Set: latin1 (legacy compatibility)
Collation: latin1_swedish_ci
Storage Engine: InnoDB
Total Size: ~2MB (sample data)

Table Specifications:
├── customers: 122 records, ~15KB
├── employees: 23 records, ~3KB
├── offices: 7 records, ~1KB  
├── orders: 326 records, ~12KB
├── orderdetails: 2,996 records, ~150KB
├── products: 110 records, ~25KB
├── productlines: 7 records, ~8KB
└── payments: 273 records, ~15KB
```
#### **API Configuration & Performance**

##### **API Specifications**
```javascript
API Configuration:
├── Base URL: http://localhost:3000/api
├── Response Format: JSON
├── HTTP Methods: GET (read-only)
├── Authentication: None (development)
├── Rate Limiting: Not implemented
├── CORS: Enabled for all origins
├── Compression: gzip enabled
└── Timeout: 30 seconds
```

##### **Standard Response Format**
Semua API responses menggunakan format JSON konsisten:
```json
{
  "success": true,
  "data": [...],           // Array of objects atau single object
  "count": 10,             // Optional: jumlah records
  "message": "string",     // Optional: additional info
  "filters": {...},        // Optional: applied filters
  "pagination": {...}      // Optional: pagination info
}
```

**Error Response Format**:
```json
{
  "success": false,
  "error": "Error message",
  "message": "Detailed description",
  "timestamp": "2024-12-10T10:30:00.000Z"
}
```

### **Endpoint Categories Overview**

| **Category** | **Endpoints** | **Primary Function** | **Key Features** |
|-------------|---------------|---------------------|------------------|
| **Customers** | 15 endpoints | Customer analytics & management | Segmentation, credit analysis, geographic distribution |
| **Products** | 13 endpoints | Product & inventory analytics | Vendor analysis, stock management, customer preferences |
| **Orders** | 11 endpoints | Order processing & trends | Status tracking, delivery analysis, temporal trends |
| **Payments** | 10 endpoints | Financial analytics | Revenue analysis, payment patterns, customer behavior |
| **Employees** | 9 endpoints | HR analytics & management | Performance tracking, hierarchy, assignments |
| **Offices** | 6 endpoints | Location analytics | Geographic distribution, employee allocation |
| **Product Lines** | 4 endpoints | Category management | Product categorization, line performance |

### **Detailed Endpoint Documentation**

#### **Customers Endpoints**

**Basic Operations**:
```http
GET /api/customers
Description: Mendapatkan semua data customers
Response: Array of 122 customer records dengan full details

GET /api/customers/total
Description: Mendapatkan total jumlah customers
Response: {"total_customers": 122}

GET /api/customers/fullname  
Description: Customers dengan nama lengkap (first + last name)
Response: Array dengan formatted fullName field
```

**Geographic Analytics**:
```http
GET /api/customers/top-country
Description: Negara dengan jumlah customers terbanyak
Response: Single object dengan country dan Total_Customers

GET /api/customers/top-city
Description: 2 kota dengan customers terbanyak
Response: Array of top 2 cities dengan customer counts

GET /api/customers/top-state
Description: State dengan customers terbanyak
Response: Single object dengan state analysis
```

**Credit Analytics**:
```http
GET /api/customers/credit-limit?min=50000&max=200000
Description: Filter customers berdasarkan credit limit range
Parameters: min (default: 50000), max (default: 200000)
Response: Array customers dalam range tersebut

GET /api/customers/highest-credit
Description: Customer dengan credit limit tertinggi
Response: Single customer object dengan highest credit

GET /api/customers/lowest-credit
Description: Customer dengan credit limit terendah
Response: Single customer object dengan lowest credit
```

**Advanced Analytics**:
```http
GET /api/customers/without-sales-rep
Description: Customers tanpa sales representative
Response: Array customers dengan salesRepEmployeeNumber NULL

GET /api/customers/credit-status
Description: Kategorisasi customers berdasarkan credit limit
Response: Array dengan credit status categories

GET /api/customers/:customerName/details
Description: Detail customer menggunakan stored procedure
Response: Comprehensive customer details via database procedure
```

#### **Products Endpoints**

**Inventory Management**:
```http
GET /api/products
Description: Semua data products dengan specifications
Response: Array of 110 product records

GET /api/products/total
Description: Total jumlah products
Response: {"Total_Products": 110}

GET /api/products/low-stock?threshold=1000
Description: Products dengan stock rendah
Response: Array products dengan quantityInStock < threshold
```

**Vendor Analytics**:
```http
GET /api/products/vendors/total
Description: Total unique vendors
Response: {"Total_Vendors": count}

GET /api/products/by-vendor
Description: Products grouped by vendor dengan statistics
Response: Array dengan vendor performance metrics

GET /api/products/price-range?minPrice=0&maxPrice=1000
Description: Products dalam range harga tertentu
Response: Array products dengan price filtering
```

**Customer Analytics**:
```http
GET /api/products/customer/:customerName
Description: Products yang dibeli oleh customer tertentu
Response: Array products dengan customer relationship

GET /api/products/most-customers
Description: Product dengan jumlah customers terbanyak
Response: Product dengan customer statistics
```

#### **Orders Endpoints**

**Trend Analysis**:
```http
GET /api/orders/by-year-month
Description: Orders trend berdasarkan tahun dan bulan
Response: Array dengan monthly breakdown dan running totals
Key Fields: Year, Month, Month_Name, Total_orders, Sum_Of_Orders

GET /api/orders/shipped-by-year
Description: Shipped orders per tahun
Response: Array dengan yearly shipping statistics

GET /api/orders/count-by-customer
Description: Jumlah orders per customer
Response: Array sorted by order count descending
```

**Status Analytics**:
```http
GET /api/orders/shipped
Description: Total orders dengan status 'Shipped'
Response: Count of shipped orders

GET /api/orders/status/:status
Description: Orders dengan status tertentu
Response: Array orders filtered by status

GET /api/orders/on-hold
Description: Orders dengan status 'On Hold' dengan details
Response: Array dengan customer dan product information
```

**Delivery Analytics**:
```http
GET /api/orders/delivery-time
Description: Analisis waktu pengiriman customer
Response: Array dengan customer name dan Total_Days
Calculation: DATEDIFF(shippedDate, orderDate)
```

#### **Payments Endpoints**

**Financial Analytics**:
```http
GET /api/payments/statistics
Description: Comprehensive payment statistics
Response: Object dengan total_payments, total_amount, average_amount, 
         min_amount, max_amount, earliest_payment, latest_payment

GET /api/payments/by-year
Description: Payment trends per tahun
Response: Array dengan Year, Total_Amount, Sum_Of_Amount

GET /api/payments/by-year-month
Description: Monthly payment breakdown
Response: Array dengan Year, Month_Name, Total_Amount
```

**Customer Analytics**:
```http
GET /api/payments/top-customers?limit=10
Description: Top paying customers
Response: Array customers dengan Total_Payment dan Payment_Count

GET /api/payments/above-average
Description: Customers dengan payments di atas rata-rata
Response: Array customers exceeding average payment amount

GET /api/payments/customer/:customerNumber
Description: Payment history untuk customer tertentu
Response: Array payments dengan customer details
```

### **Query Performance Guidelines**

#### **Response Time Expectations**
| **Query Type** | **Expected Response Time** | **Data Volume** |
|---------------|---------------------------|-----------------|
| Simple lookups | <100ms | <1KB |
| Basic analytics | 100-300ms | 1-10KB |
| Complex aggregations | 300-1000ms | 10-50KB |
| Multi-table JOINs | 200-500ms | 5-25KB |

#### **Optimization Tips**
- Use specific endpoints instead of fetching all data
- Implement client-side caching for static data
- Use pagination parameters where available
- Monitor response times dan optimize queries accordingly

---

## **Deployment**

### **Deployment Strategy**
Sistem P2-OC-API dirancang untuk deployment yang fleksibel dengan berbagai strategi:

#### **Local Development**
```bash
# Clone repository
git clone <repository-url>
cd p2-oc-api

# Install dependencies
npm install

# Setup environment
cp .env.example .env

# Start with Docker
docker compose up --build
```

#### **Production Deployment**
```bash
# Production deployment dengan Docker
docker compose -f docker-compose.prod.yml up -d

# Atau manual deployment
npm install --production
NODE_ENV=production pm2 start server.js
```

### **Server Requirements**
- **Minimum Hardware**: 2 CPU cores, 4GB RAM, 20GB storage
- **Recommended Hardware**: 4 CPU cores, 8GB RAM, 50GB SSD
- **Operating System**: Linux Ubuntu 20.04+ atau CentOS 8+
- **Network**: Port 3000 (API), Port 3306 (MySQL)

### **Performance Monitoring**
```bash
# Health check endpoint
curl http://localhost:3000/health

# Performance metrics
curl http://localhost:3000/api/stats/performance
```


### **Testing & Business Intelligence**

### **Testing Overview**
Proyek ini mencakup berbagai tingkat pengujian untuk memastikan kualitas dan keandalan sistem:

- **Unit Testing**: Pengujian fungsi dan metode individual
- **Integration Testing**: Pengujian integrasi antar modul dan komponen
- **API Testing**: Pengujian fungsionalitas endpoint API
- **Performance Testing**: Pengujian beban dan respons sistem
- **Security Testing**: Pengujian kerentanan dan validasi input

### **Performance Testing**
```bash
# Install artillery untuk load testing
npm install -g artillery

# Run load test
artillery quick --count 100 --num 10 http://localhost:3000/api/customers
```

### **Database Testing**
```sql
-- Validate data integrity
SELECT 
    COUNT(*) as total_customers,
    COUNT(DISTINCT customerNumber) as unique_customers
FROM customers;

-- Performance testing query
EXPLAIN SELECT * FROM orders 
WHERE orderDate BETWEEN '2003-01-01' AND '2005-12-31'
ORDER BY orderDate DESC;
```

### **Kesimpulan**

### **Kesimpulan**
P2-OC-API telah berhasil dikembangkan sebagai sistem REST API yang komprehensif dengan karakteristik sebagai berikut:

- **Arsitektur yang Solid**: Implementasi 3-tier architecture dengan separation of concerns yang jelas
- **Scalability**: Sistem dapat menangani high-traffic dengan performance yang konsisten
- **Maintainability**: Kode terorganisir dengan good practices dan comprehensive documentation
- **Business Value**: Menyediakan insight bisnis yang valuable melalui 68 analytical endpoints
- **Modern Technology Stack**: Menggunakan teknologi terkini yang industry-standard



## **Referensi dan Sumber**

### **Technical References**
- **Node.js Documentation**. (2024). *Node.js Official Documentation*. https://nodejs.org/docs/
- **Express.js Guide**. (2024). *Express.js Framework Documentation*. https://expressjs.com/
- **MySQL Documentation**. (2024). *MySQL 8.0 Reference Manual*. https://dev.mysql.com/doc/
- **Docker Documentation**. (2024). *Docker Official Documentation*. https://docs.docker.com/
- **REST API Design Best Practices**. (2024). *RESTful API Design Guidelines*

### **Academic References**
- Fielding, R. T. (2000). *Architectural Styles and the Design of Network-based Software Architectures*. Doctoral dissertation, University of California, Irvine.
- Richardson, L., & Ruby, S. (2013). *RESTful Web APIs: Services for a Changing World*. O'Reilly Media.
- Newman, S. (2021). *Building Microservices: Designing Fine-Grained Systems*. O'Reilly Media.
- Fowler, M. (2018). *Patterns of Enterprise Application Architecture*. Addison-Wesley Professional.

### **Tools and Libraries**
```json
{
  "runtime": "Node.js v18.17.0",
  "framework": "Express.js v4.18.2",
  "database": "MySQL v8.0.33",
  "containerization": "Docker v24.0.2",
  "documentation": "Swagger/OpenAPI v3.0",
  "testing": "Jest v29.5.0",
  "monitoring": "Winston v3.8.2"
}
```


### **A. Environment Variables**
```env
# Database Configuration
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=password
DB_NAME=classicmodels

# Application Configuration
NODE_ENV=development
PORT=3000
API_VERSION=v1

# Security Configuration
JWT_SECRET=your-secret-key
RATE_LIMIT_WINDOW=15
RATE_LIMIT_MAX=100
```

### **B. Database Schema Diagram**
![alt text](db.svg)

### **C. API Response Format Standards**
```json
{
  "success": true,
  "message": "Operation completed successfully",
  "data": {
    "items": [...],
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 100,
      "pages": 10
    }
  },
  "meta": {
    "timestamp": "2024-06-12T10:30:00Z",
    "version": "1.0.0",
    "endpoint": "/api/customers"
  }
}
```

---
