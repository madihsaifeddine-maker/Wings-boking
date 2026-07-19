-- الجدول الأساسي للمنتجات
CREATE TABLE Products (
  product_id SERIAL PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  description TEXT,
  product_type ENUM('print_book','color_card','bundle','download_pack') NOT NULL,
  price DECIMAL(10,2) NOT NULL,
  currency VARCHAR(3) DEFAULT 'USD',
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- الفئات/الأقسام
CREATE TABLE Categories (
  category_id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  parent_id INT REFERENCES Categories(category_id)
);

-- ربط المنتجات بالفئات
CREATE TABLE ProductCategories (
  product_id INT REFERENCES Products(product_id),
  category_id INT REFERENCES Categories(category_id),
  PRIMARY KEY (product_id, category_id)
);

-- تفاصيل الإصدار/النسخ
CREATE TABLE Variants (
  variant_id SERIAL PRIMARY KEY,
  product_id INT REFERENCES Products(product_id),
  variant_name VARCHAR(100),
  price DECIMAL(10,2),
  stock INT,
  sku VARCHAR(50),
  is_primary BOOLEAN DEFAULT FALSE
);

-- محتوى الصفحات (مثلاً table of contents، صفحات تلوين، بطاقات)
CREATE TABLE ContentPages (
  page_id SERIAL PRIMARY KEY,
  product_id INT REFERENCES Products(product_id),
  page_number INT,
  content_type ENUM('color_page','activity','solution','cover','toc','intro','banner'),
  content_text TEXT,
  asset_path VARCHAR(255) -- مسار ملف الصورة/PDF/أصل المحتوى
);

-- بطاقات نشاط قابلة للتحميل
CREATE TABLE DownloadPack (
  pack_id SERIAL PRIMARY KEY,
  product_id INT REFERENCES Products(product_id),
  name VARCHAR(100),
  description TEXT
);

CREATE TABLE DownloadItems (
  item_id SERIAL PRIMARY KEY,
  pack_id INT REFERENCES DownloadPack(pack_id),
  title VARCHAR(100),
  content_type ENUM('color','word_search','crossword','match','maze','other'),
  pdf_path VARCHAR(255),
  price DECIMAL(10,2) DEFAULT 0.00
);

-- المستخدمين/الزبناء
CREATE TABLE Customers (
  customer_id SERIAL PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL,
  name VARCHAR(100),
  created_at TIMESTAMP DEFAULT NOW()
);

-- الطلبات
CREATE TABLE Orders (
  order_id SERIAL PRIMARY KEY,
  customer_id INT REFERENCES Customers(customer_id),
  total_amount DECIMAL(10,2),
  currency VARCHAR(3) DEFAULT 'USD',
  status ENUM('pending','paid','shipped','completed','refunded') DEFAULT 'pending',
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE TABLE OrderItems (
  order_item_id SERIAL PRIMARY KEY,
  order_id INT REFERENCES Orders(order_id),
  product_id INT REFERENCES Products(product_id),
  quantity INT DEFAULT 1,
  unit_price DECIMAL(10,2)
);

-- التنزيلات الرقمية للمستخدمين
CREATE TABLE Downloads (
  download_id SERIAL PRIMARY KEY,
  order_item_id INT REFERENCES OrderItems(order_item_id),
  customer_id INT REFERENCES Customers(customer_id),
  file_path VARCHAR(255),
  expires_at TIMESTAMP
);
