# Generative AI for Software Testing - Chi tiết bài học

## Khởi đầu khoá học

### Tổng quan khoá học

**Đối tượng:** QA Engineers, Automation Testers, Test Architects

**Mục tiêu:** Ứng dụng Generative AI để hỗ trợ kiểm thử phần mềm hàng ngày

**Yêu cầu đầu vào:**
- Kiến thức cơ bản về kiểm thử phần mềm
- Kỹ năng sử dụng công cụ như Postman, VS Code, Git
- Kỹ năng Python cơ bản (tuỳ chọn nhưng khuyến nghị)

**Thời lượng:** 4 sessions (16 giờ)

---

## Session 1: Introduction to Generative AI in Testing

### 1.1. Overview of Generative AI

#### Lý thuyết (45 phút)

**Generative AI là gì?**
- Định nghĩa: AI có khả năng tạo ra nội dung mới (văn bản, code, hình ảnh) dựa trên dữ liệu đã học
- Khác biệt với AI truyền thống: Thay vì chỉ phân loại/dự đoán, GenAI có thể sáng tạo nội dung

**So sánh AI truyền thống vs GenAI:**

| Tiêu chí | AI Truyền thống | Generative AI |
|----------|-----------------|---------------|
| Mục đích | Phân loại, dự đoán | Tạo nội dung mới |
| Đầu ra | Nhãn, số, phân loại | Văn bản, code, hình ảnh |
| Ứng dụng testing | Phát hiện bug, phân loại lỗi | Tạo test case, sinh dữ liệu test |

**Large Language Models (LLMs):**
- Cấu trúc: Transformer architecture
- Training process: Pre-training → Fine-tuning
- Cách hoạt động: Token prediction

**Hạn chế quan trọng:**
- **Token limit:** Giới hạn độ dài input/output
- **Context window:** Không thể "nhớ" thông tin ngoài cuộc hội thoại hiện tại
- **Hallucination:** Tạo ra thông tin không chính xác nhưng có vẻ hợp lý

#### Thực hành (45 phút)

**Bài tập 1: Phân tích Hallucination**
```
Prompt: "Hãy tạo một test case cho tính năng thanh toán của ứng dụng XYZ (ứng dụng không tồn tại)"

Quan sát:
- AI sẽ tạo ra test case có vẻ hợp lý
- Nhưng các chi tiết cụ thể có thể không chính xác
- Phân tích: Đâu là thông tin "hallucination"?
```

**Bài tập 2: Context Window Test**
```
1. Cung cấp một đoạn requirements dài (> 2000 từ)
2. Hỏi về chi tiết ở đầu đoạn
3. Quan sát khả năng "nhớ" của AI
```

### 1.2. Popular AI Models and Their Usage

#### Lý thuyết (30 phút)

**Tổng quan các mô hình:**

| Model | Provider | Strengths | Best for Testing |
|-------|----------|-----------|------------------|
| GPT-4/4o | OpenAI | Reasoning, coding | Test case generation |
| Claude | Anthropic | Long context, analysis | Requirements analysis |
| Gemini | Google | Multimodal | UI testing scenarios |
| LLaMA | Meta | Open-source | Custom fine-tuning |
| Copilot | Microsoft | Code completion | Test automation |

**Ứng dụng cụ thể:**
- **GPT-4:** Sinh test case phức tạp, API testing
- **Claude:** Phân tích tài liệu requirements dài
- **Gemini:** Kết hợp text + image cho UI testing
- **Copilot:** Hỗ trợ viết automation scripts

#### Thực hành (60 phút)

**Setup Environment:**

1. **Tạo accounts:**
   ```
   - ChatGPT Plus (openai.com)
   - Claude Pro (claude.ai)
   - Gemini Advanced (gemini.google.com)
   ```

2. **So sánh outputs:**
   ```
   Prompt: "Generate 5 test cases for a login functionality with username/password"
   
   Tiêu chí đánh giá:
   - Độ chi tiết
   - Coverage (positive, negative, edge cases)
   - Cấu trúc test case
   - Practicality
   ```

**Kết quả mong đợi:**
- Hiểu được điểm mạnh/yếu của từng model
- Biết khi nào dùng model nào

### 1.3. Setting Up AI Tools for Testing

#### Lý thuyết (30 phút)

**API Configuration:**
```python
# OpenAI API Setup
pip install openai
export OPENAI_API_KEY="your-api-key"

# Basic usage
from openai import OpenAI
client = OpenAI()

response = client.chat.completions.create(
    model="gpt-4",
    messages=[{"role": "user", "content": "Generate a test case"}]
)
```

**Development Tools:**
- **VS Code:** IDE chính
- **GitHub Copilot:** AI pair programming
- **AWS CodeWhisperer:** Alternative to Copilot
- **Cursor:** AI-first code editor

#### Thực hành (60 phút)

**Lab 1: VS Code + Copilot Setup**
```bash
# 1. Install VS Code extensions
- GitHub Copilot
- Python
- Playwright Test for VS Code

# 2. Enable Copilot
- Sign in with GitHub account
- Test with simple Python function
```

**Lab 2: First AI-Assisted Code**
```python
# Prompt for Copilot: "Create a function to validate email format"
# Let Copilot suggest the implementation
# Then ask for test cases for this function

def validate_email(email):
    # Copilot will suggest implementation
    pass

def test_validate_email():
    # Copilot will suggest test cases
    pass
```

**Lab 3: OpenAI API Integration**
```python
# File: ai_helper.py
import openai

class TestAIHelper:
    def __init__(self, api_key):
        self.client = openai.OpenAI(api_key=api_key)
    
    def generate_test_case(self, feature_description):
        prompt = f"""

**Lab 2: Advanced Data Quality Validation**

```python
# Comprehensive data validation prompt
quality_validation_prompt = """
Create a comprehensive data quality validation script for e-commerce test data.

VALIDATION REQUIREMENTS:

1. SCHEMA VALIDATION:
   - All required fields present
   - Correct data types
   - Format constraints (email, phone, dates)
   - Value ranges (prices > 0, valid status codes)

2. BUSINESS RULES:
   - Order total = sum of line items + tax - discounts
   - Can't have orders for inactive users
   - Inventory levels make sense
   - Shipping address required for shipped orders

3. DATA QUALITY:
   - No duplicate primary keys
   - Referential integrity (foreign keys exist)
   - Realistic value distributions
   - No obvious test artifacts ("test@test.com")

4. EDGE CASES:
   - Handle null/empty values
   - Unicode characters in names
   - Very large/small numeric values
   - Date boundaries (leap years, timezones)

Generate Python code using pandas and custom validation functions.
Include detailed reporting of all issues found.
"""

# Advanced validation implementation
advanced_validation = """
import pandas as pd
import re
from datetime import datetime, date
from typing import Dict, List, Any
import numpy as np

class TestDataValidator:
    def __init__(self):
        self.issues = []
        self.warnings = []
        
    def validate_ecommerce_dataset(self, users_df: pd.DataFrame, 
                                 products_df: pd.DataFrame, 
                                 orders_df: pd.DataFrame) -> Dict[str, Any]:
        
        results = {
            'users': self._validate_users(users_df),
            'products': self._validate_products(products_df),
            'orders': self._validate_orders(orders_df),
            'relationships': self._validate_relationships(users_df, products_df, orders_df),
            'business_rules': self._validate_business_rules(users_df, products_df, orders_df)
        }
        
        return results
    
    def _validate_users(self, df: pd.DataFrame) -> Dict[str, List[str]]:
        issues = []
        
        # Required fields
        required_fields = ['id', 'email', 'firstName', 'lastName']
        for field in required_fields:
            if field not in df.columns:
                issues.append(f"Missing required column: {field}")
            elif df[field].isnull().any():
                null_count = df[field].isnull().sum()
                issues.append(f"{field} has {null_count} null values")
        
        # Email validation
        if 'email' in df.columns:
            email_pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}
        Generate detailed test cases for: {feature_description}
        Format: Given-When-Then
        Include: Positive, Negative, Edge cases
        """
        
        response = self.client.chat.completions.create(
            model="gpt-4",
            messages=[{"role": "user", "content": prompt}]
        )
        
        return response.choices[0].message.content

# Test the helper
helper = TestAIHelper("your-api-key")
test_cases = helper.generate_test_case("User login with email and password")
print(test_cases)
```

---

## Session 2: AI-Assisted Test Case Generation

### 2.1. Using Generative AI to Generate Test Cases

#### Lý thuyết (60 phút)

**Prompt Engineering cho Testing:**

**Cấu trúc Prompt hiệu quả:**
1. **Context:** Mô tả hệ thống/tính năng
2. **Task:** Yêu cầu cụ thể
3. **Format:** Định dạng mong muốn
4. **Constraints:** Ràng buộc/yêu cầu đặc biệt

```
Template:
"""
CONTEXT: [Mô tả hệ thống/tính năng]
TASK: Generate test cases for [specific functionality]
FORMAT: 
- Test Case ID
- Title
- Preconditions
- Steps
- Expected Results
CONSTRAINTS:
- Include positive, negative, and edge cases
- Focus on [specific aspects]
"""
```

**RAG (Retrieval-Augmented Generation):**
- Định nghĩa: Kết hợp thông tin từ database/documents với LLM
- Lợi ích: Giảm hallucination, tăng accuracy
- Ứng dụng: Sử dụng existing test cases, requirements documents

**RAG Architecture:**
```
Documents → Vector DB → Retrieval → LLM → Enhanced Output
```

#### Thực hành (90 phút)

**Lab 1: Basic Test Case Generation**

```python
# Prompt Templates
basic_prompt = """
Generate test cases for a login feature with the following requirements:
- Users can login with email/username and password
- System should validate credentials
- Failed attempts should be tracked
- Account locks after 3 failed attempts

Format each test case as:
ID: TC_XXX
Title: [Clear title]
Preconditions: [What needs to be ready]
Steps: [Numbered steps]
Expected: [Expected outcome]
"""

advanced_prompt = """
CONTEXT: E-commerce web application with user authentication
FEATURE: Login functionality
REQUIREMENTS:
- Support email and username login
- Password complexity validation
- Remember me option
- Social login (Google, Facebook)
- Account lockout policy
- Password reset flow

TASK: Generate comprehensive test cases covering:
1. Functional testing (positive flows)
2. Negative testing (invalid inputs)
3. Security testing (injection, brute force)
4. UI/UX testing (responsive, accessibility)
5. Integration testing (SSO, password reset)

FORMAT: Gherkin syntax (Given-When-Then)
CONSTRAINTS: 
- Minimum 15 test cases
- Cover all requirements
- Include data-driven scenarios
"""
```

**Lab 2: RAG Implementation**

```python
# Simple RAG for test case generation
import json
from typing import List

class TestCaseRAG:
    def __init__(self):
        self.knowledge_base = {
            "login_requirements": [
                "Email/username authentication",
                "Password complexity: min 8 chars, special chars",
                "Account lockout after 3 failed attempts",
                "Session timeout after 30 minutes"
            ],
            "existing_test_cases": [
                {
                    "id": "TC_001",
                    "title": "Valid login with email",
                    "steps": ["Enter valid email", "Enter valid password", "Click login"],
                    "expected": "User logged in successfully"
                }
            ],
            "common_test_patterns": [
                "Boundary value testing",
                "Equivalence partitioning",
                "State transition testing"
            ]
        }
    
    def retrieve_context(self, query: str) -> str:
        # Simple keyword matching (in real implementation, use vector search)
        context = []
        if "login" in query.lower():
            context.extend(self.knowledge_base["login_requirements"])
            context.extend([tc["title"] for tc in self.knowledge_base["existing_test_cases"]])
        
        return "\n".join(context)
    
    def generate_with_rag(self, feature_description: str) -> str:
        context = self.retrieve_context(feature_description)
        
        prompt = f"""
        CONTEXT INFORMATION:
        {context}
        
        TASK: Generate new test cases for: {feature_description}
        
        REQUIREMENTS:
        - Don't duplicate existing test cases
        - Follow established patterns
        - Consider all requirements mentioned in context
        
        FORMAT: Gherkin scenarios
        """
        
        # In real implementation, call OpenAI API here
        return prompt

# Usage
rag = TestCaseRAG()
enhanced_prompt = rag.generate_with_rag("Login functionality testing")
print(enhanced_prompt)
```

### 2.2. Refining AI-Generated Test Cases

#### Lý thuyết (45 phút)

**Phân tích chất lượng Test Cases:**

**Tiêu chí đánh giá:**
1. **Coverage:** Có đủ positive, negative, edge cases?
2. **Clarity:** Test steps có rõ ràng, dễ hiểu?
3. **Executability:** Có thể thực hiện được không?
4. **Traceability:** Link với requirements?
5. **Maintainability:** Dễ cập nhật khi cần?

**Common Issues với AI-generated test cases:**
- Thiếu context cụ thể của hệ thống
- Test data không realistic
- Missing edge cases
- Over-complicated scenarios
- Không follow testing standards

**Improvement Strategies:**
1. **Iterative Prompting:** Cải thiện dần qua nhiều lần
2. **Domain Knowledge Injection:** Bổ sung thông tin chuyên môn
3. **Template Standardization:** Sử dụng template chuẩn
4. **Human Review:** Kết hợp với kinh nghiệm tester

#### Thực hành (75 phút)

**Lab 1: Test Case Quality Analysis**

```python
# AI-generated test case example (deliberately flawed)
ai_generated = """
Test Case: Login Test
1. Go to login page
2. Enter username
3. Enter password
4. Click login
5. Verify login successful
"""

# Improvement process
improvement_prompt = """
Improve this test case with the following requirements:
- Add specific test data
- Include preconditions and postconditions
- Add negative scenarios
- Make steps more detailed
- Add expected results for each step

Original test case:
{ai_generated}

Business context:
- This is for a banking application
- Security is critical
- Users can login with account number or email
- 2FA is required for first-time devices
"""

improved_prompt = f"""
CONTEXT: Banking application login testing
ORIGINAL TEST CASE: {ai_generated}

IMPROVEMENTS NEEDED:
1. Add specific, realistic test data
2. Include security considerations
3. Add preconditions/postconditions
4. Create both positive and negative scenarios
5. Consider 2FA flow
6. Add validation points

REQUIREMENTS:
- Follow banking security standards
- Include accessibility testing
- Consider mobile responsiveness
- Add performance expectations

OUTPUT FORMAT:
Test Case ID: [Unique ID]
Title: [Descriptive title]
Priority: [High/Medium/Low]
Preconditions: [Setup requirements]
Test Data: [Specific data to use]
Steps: [Detailed numbered steps]
Expected Results: [Clear expected outcomes]
Postconditions: [Cleanup requirements]
"""
```

**Lab 2: Domain Knowledge Enhancement**

```python
# Domain-specific enhancement
banking_context = """
BANKING DOMAIN KNOWLEDGE:
- Account numbers: 10-12 digits
- Password policy: 8-16 chars, uppercase, lowercase, numbers, special chars
- Session timeout: 15 minutes of inactivity
- Login attempts: Max 3 before account lock
- 2FA: SMS OTP or authenticator app
- Regulatory compliance: PCI DSS, SOX
- Audit trail: All login attempts logged

COMMON BANKING TEST SCENARIOS:
- Joint account access
- Corporate account delegation
- International character support
- Accessibility compliance (WCAG 2.1)
- Browser compatibility
- Network interruption handling
"""

enhanced_prompt = f"""
{banking_context}

Generate banking-specific login test cases considering:
1. Regulatory compliance requirements
2. Security best practices
3. Accessibility standards
4. Multi-device scenarios
5. Edge cases specific to banking

Focus on scenarios that are unique to banking domain.
"""
```

### 2.3. Automation Readiness of AI-Generated Test Cases

#### Lý thuyết (30 phút)

**Converting Test Cases to Automation:**

**Automation Readiness Checklist:**
- [ ] Test steps are specific and unambiguous
- [ ] Test data is clearly defined
- [ ] UI elements are identifiable
- [ ] Expected results are verifiable
- [ ] Dependencies are minimal

**Automation Patterns:**
1. **Page Object Model:** Organize UI interactions
2. **Data-Driven Testing:** Parameterize test data
3. **Behavior-Driven Development:** Gherkin scenarios
4. **API Testing:** REST/GraphQL test patterns

#### Thực hành (90 phút)

**Lab 1: Test Case to Playwright Conversion**

```python
# Original AI-generated test case
test_case = """
Test Case: User Login
Given user is on login page
When user enters valid email "user@test.com"
And user enters valid password "Test123!"
And user clicks login button
Then user should be redirected to dashboard
And welcome message should display user's name
"""

# AI prompt for Playwright conversion
conversion_prompt = f"""
Convert this test case to Playwright automation code:

{test_case}

Requirements:
- Use Page Object Model pattern
- Include proper waits and assertions
- Add error handling
- Use data-driven approach
- Follow Playwright best practices

Generate:
1. Page Object class
2. Test specification
3. Test data file
"""

# Expected output structure:
playwright_structure = """
# pages/login_page.py
class LoginPage:
    def __init__(self, page):
        self.page = page
        self.email_input = page.locator('[data-testid="email"]')
        self.password_input = page.locator('[data-testid="password"]')
        self.login_button = page.locator('[data-testid="login-btn"]')
    
    async def login(self, email, password):
        await self.email_input.fill(email)
        await self.password_input.fill(password)
        await self.login_button.click()

# tests/test_login.py
import pytest
from pages.login_page import LoginPage
from pages.dashboard_page import DashboardPage

@pytest.mark.asyncio
async def test_valid_login(page, test_data):
    login_page = LoginPage(page)
    dashboard_page = DashboardPage(page)
    
    await page.goto("/login")
    await login_page.login(test_data["email"], test_data["password"])
    
    await expect(page).to_have_url("/dashboard")
    await expect(dashboard_page.welcome_message).to_contain_text(test_data["expected_name"])

# test_data.json
{
    "valid_user": {
        "email": "user@test.com",
        "password": "Test123!",
        "expected_name": "John Doe"
    }
}
"""
```

**Lab 2: API Test Generation**

```python
# AI prompt for API test generation
api_test_prompt = """
Generate API test cases for login endpoint:

ENDPOINT: POST /api/auth/login
REQUEST BODY:
{
    "email": "string",
    "password": "string",
    "remember_me": "boolean"
}

RESPONSES:
200: {"token": "jwt_token", "user": {...}}
400: {"error": "Invalid credentials"}
429: {"error": "Too many attempts"}

Generate:
1. Postman collection
2. Python requests test
3. Playwright API test
4. Test data variations

Include:
- Happy path scenarios
- Error handling
- Security testing
- Performance considerations
"""

# Expected API test structure
api_test_example = """
# tests/api/test_auth.py
import pytest
import requests
from playwright.sync_api import APIRequestContext

class TestAuthAPI:
    base_url = "https://api.example.com"
    
    def test_valid_login_requests(self):
        url = f"{self.base_url}/api/auth/login"
        payload = {
            "email": "valid@test.com",
            "password": "ValidPass123!"
        }
        
        response = requests.post(url, json=payload)
        
        assert response.status_code == 200
        assert "token" in response.json()
        assert response.json()["user"]["email"] == payload["email"]
    
    @pytest.mark.asyncio
    async def test_invalid_login_playwright(self, api_context: APIRequestContext):
        response = await api_context.post(f"{self.base_url}/api/auth/login", data={
            "email": "invalid@test.com",
            "password": "wrong_password"
        })
        
        assert response.status == 400
        body = await response.json()
        assert "error" in body
"""
```

---

## Session 3: AI-Powered Test Data Generation

### 3.1. Introduction to AI-Driven Test Data Creation

#### Lý thuyết (45 phút)

**Tại sao Test Data quan trọng:**
- Chiếm 30-40% effort trong testing
- Ảnh hưởng trực tiếp đến test coverage
- Quyết định chất lượng của test execution
- Critical cho performance và security testing

**Challenges với Traditional Data Generation:**
- Time-consuming manual creation
- Limited variety and edge cases
- Privacy concerns with production data
- Maintenance overhead
- Consistency across environments

**AI Advantages:**
- Generate large volumes quickly
- Create realistic, diverse data
- Handle complex relationships
- Generate edge cases automatically
- Maintain data privacy

**Types of Test Data:**
1. **Master Data:** Users, products, categories
2. **Transactional Data:** Orders, payments, logs
3. **Reference Data:** Countries, currencies, codes
4. **Configuration Data:** Settings, parameters

#### Thực hành (45 phút)

**Lab 1: Basic Data Generation**

```python
# Simple user data generation prompt
user_data_prompt = """
Generate 10 realistic user profiles for testing an e-commerce application.

Requirements:
- Diverse demographics (age, location, occupation)
- Realistic names from different cultures
- Valid email formats
- Phone numbers in US format
- Mix of customer types (new, returning, premium)

Format: JSON array with fields:
- id, firstName, lastName, email, phone, dateOfBirth, address, customerType, registrationDate

Ensure data looks realistic and could pass basic validation.
"""

# Advanced data generation with relationships
complex_data_prompt = """
Generate a complete e-commerce test dataset including:

USERS (5 users):
- Personal information
- Address details
- Payment methods
- Order history

PRODUCTS (20 products):
- Different categories
- Price ranges
- Inventory levels
- Ratings and reviews

ORDERS (15 orders):
- Link to existing users
- Multiple products per order
- Different order statuses
- Realistic timestamps

Requirements:
- Maintain referential integrity
- Include edge cases (empty cart, high-value orders)
- Mix of payment methods
- Various shipping addresses
- Realistic product names and descriptions

Output: Separate JSON files for each entity type
"""
```

### 3.2. Generating Test Data with Generative AI

#### Lý thuyết (30 phút)

**Schema-Driven Generation:**
- OpenAPI/Swagger specifications
- Database schemas (SQL DDL)
- JSON Schema validation
- XML Schema (XSD)

**Data Formats:**
- **JSON:** API testing, NoSQL databases
- **CSV:** Bulk imports, Excel integration
- **XML:** Legacy systems, configuration files
- **SQL:** Database seeding

**Advanced Techniques:**
- **Constraint satisfaction:** Business rules compliance
- **Relationship modeling:** Foreign key integrity
- **Temporal data:** Time-series, historical data
- **Localization:** Multi-language, regional formats

#### Thực hành (90 phút)

**Lab 1: Schema-Based Generation**

```python
# OpenAPI schema example
openapi_schema = """
User:
  type: object
  required:
    - id
    - email
    - firstName
    - lastName
  properties:
    id:
      type: integer
      minimum: 1
    email:
      type: string
      format: email
    firstName:
      type: string
      minLength: 1
      maxLength: 50
    lastName:
      type: string
      minLength: 1
      maxLength: 50
    dateOfBirth:
      type: string
      format: date
    phoneNumber:
      type: string
      pattern: '^\\+?[1-9]\\d{1,14}$'
    address:
      $ref: '#/components/schemas/Address'

Address:
  type: object
  properties:
    street:
      type: string
    city:
      type: string
    state:
      type: string
    zipCode:
      type: string
      pattern: '^\\d{5}(-\\d{4})?$'
    country:
      type: string
      enum: ['US', 'CA', 'UK', 'DE', 'FR']
"""

schema_prompt = f"""
Based on this OpenAPI schema:

{openapi_schema}

Generate 20 valid user records that:
1. Comply with all schema constraints
2. Include realistic, diverse data
3. Cover edge cases for validation testing
4. Include some boundary values (min/max lengths)
5. Represent different countries and formats

Output format: JSON array
Include comments explaining the test strategy for each edge case.
"""

# SQL Schema example
sql_schema = """
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    date_of_birth DATE,
    phone_number VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    is_active BOOLEAN DEFAULT true,
    user_type ENUM('customer', 'admin', 'moderator') DEFAULT 'customer'
);

CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    total_amount DECIMAL(10,2) NOT NULL,
    status ENUM('pending', 'confirmed', 'shipped', 'delivered', 'cancelled'),
    shipping_address TEXT,
    billing_address TEXT
);
"""

sql_data_prompt = f"""
Generate SQL INSERT statements for the following schema:

{sql_schema}

Requirements:
- 15 users with diverse profiles
- 25 orders distributed across users
- Realistic data that follows business logic
- Include various order statuses
- Some users with multiple orders, some with none
- Test boundary conditions (very old/young users, high-value orders)

Output:
1. INSERT statements for users table
2. INSERT statements for orders table
3. Comments explaining the test scenarios covered
"""
```

**Lab 2: Complex Relationship Data**

```python
# E-commerce complete dataset generation
ecommerce_prompt = """
Generate a complete e-commerce test dataset with the following entities and relationships:

USERS (10 records):
- Mix of customer types: new (2), regular (6), premium (2)
- Age distribution: 18-25 (3), 26-40 (4), 41-65 (3)
- Geographic distribution: US (6), Canada (2), UK (2)

CATEGORIES (5 categories):
- Electronics, Clothing, Books, Home & Garden, Sports

PRODUCTS (25 products):
- 5 products per category
- Price range: $10-$500
- Mix of in-stock and out-of-stock items
- Include product variants (size, color) where applicable

ORDERS (20 orders):
- Distributed across 8 users (2 users with no orders)
- Order values: $20-$800
- Status distribution: 50% delivered, 30% shipped, 15% pending, 5% cancelled
- Include multi-item orders and single-item orders

BUSINESS RULES:
- Premium customers get 10% discount
- Free shipping over $100
- Can't order out-of-stock items
- Order total must match item prices + tax - discounts

OUTPUT FORMAT:
Separate JSON files for each entity, with clear relationship keys.
Include a summary of test scenarios this data enables.
"""
```

### 3.3. Transforming and Validating Test Data

#### Lý thuyết (30 phút)

**Data Transformation Needs:**
- Format conversion (JSON ↔ CSV ↔ XML)
- Schema evolution (adding/removing fields)
- Data cleansing (removing duplicates, fixing formats)
- Anonymization (PII masking)

**Validation Strategies:**
- Schema validation
- Business rule validation
- Data quality checks
- Referential integrity

**Tools and Libraries:**
- **Pandas:** Data manipulation and analysis
- **Faker:** Realistic fake data generation
- **JSONSchema:** JSON validation
- **Pydantic:** Data modeling and validation

#### Thực hành (60 phút)

**Lab 1: Data Format Conversion**

```python
# AI prompt for data transformation
transformation_prompt = """
Convert this JSON user data to CSV format, then create SQL INSERT statements:

JSON Data:
[
    {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "address": {
            "street": "123 Main St",
            "city": "Anytown",
            "state": "CA",
            "zip": "12345"
        },
        "orders": [
            {"id": 101, "total": 99.99, "date": "2024-01-15"},
            {"id": 102, "total": 149.50, "date": "2024-02-01"}
        ]
    }
]

Requirements:
1. Flatten nested objects for CSV
2. Handle arrays (orders) appropriately
3. Generate SQL for normalized tables (users, addresses, orders)
4. Maintain referential integrity
5. Include proper data types in SQL

Output:
1. CSV format
2. SQL CREATE TABLE statements
3. SQL INSERT statements
"""

# Python validation script
validation_script = """
import json
import pandas as pd
from jsonschema import validate, ValidationError
from typing import List, Dict

def validate_user_data(data: List[Dict]) -> Dict[str, List[str]]:
    '''Validate generated user data for common issues'''
    
    issues = {
        'email_format': [],
        'duplicate_emails': [],
        'missing_required': [],
        'invalid_dates': [],
        'business_rules': []
    }
    
    emails_seen = set()
    
    for i, user in enumerate(data):
        # Check required fields
        required = ['id', 'email', 'firstName', 'lastName']
        missing = [field for field in required if field not in user or not user[field]]
        if missing:
            issues['missing_required'].append(f"User {i}: Missing {missing}")
        
        # Check email format
        email = user.get('email', '')
        if email and '@' not in email:
            issues['email_format'].append(f"User {i}: Invalid email format")
        
        # Check for duplicates
        if email in emails_seen:
            issues['duplicate_emails'].append(f"User {i}: Duplicate email {email}")
        emails_seen.add(email)
        
        # Business rule: Premium customers should have order history
        if user.get('customerType') == 'premium' and not user.get('orders'):
            issues['business_rules'].append(f"User
            invalid_emails = df[~df['email'].str.match(email_pattern, na=False)]
            if not invalid_emails.empty:
                issues.append(f"Invalid email formats: {invalid_emails['email'].tolist()}")
        
        # Duplicate emails
        if 'email' in df.columns:
            duplicates = df[df.duplicated(['email'], keep=False)]
            if not duplicates.empty:
                issues.append(f"Duplicate emails: {duplicates['email'].tolist()}")
        
        # Age validation (if date of birth present)
        if 'dateOfBirth' in df.columns:
            df['dateOfBirth'] = pd.to_datetime(df['dateOfBirth'], errors='coerce')
            today = datetime.now()
            ages = (today - df['dateOfBirth']).dt.days / 365.25
            
            invalid_ages = ages[(ages < 13) | (ages > 120)]
            if not invalid_ages.empty:
                issues.append(f"Invalid ages detected: {invalid_ages.tolist()}")
        
        return {'issues': issues, 'record_count': len(df)}
    
    def _validate_products(self, df: pd.DataFrame) -> Dict[str, List[str]]:
        issues = []
        
        # Price validation
        if 'price' in df.columns:
            invalid_prices = df[df['price'] <= 0]
            if not invalid_prices.empty:
                issues.append(f"Products with invalid prices: {invalid_prices['id'].tolist()}")
        
        # Inventory validation
        if 'inventory' in df.columns:
            negative_inventory = df[df['inventory'] < 0]
            if not negative_inventory.empty:
                issues.append(f"Products with negative inventory: {negative_inventory['id'].tolist()}")
        
        return {'issues': issues, 'record_count': len(df)}
    
    def _validate_orders(self, df: pd.DataFrame) -> Dict[str, List[str]]:
        issues = []
        
        # Order total validation
        if 'total' in df.columns:
            invalid_totals = df[df['total'] <= 0]
            if not invalid_totals.empty:
                issues.append(f"Orders with invalid totals: {invalid_totals['id'].tolist()}")
        
        # Status validation
        if 'status' in df.columns:
            valid_statuses = ['pending', 'confirmed', 'shipped', 'delivered', 'cancelled']
            invalid_status = df[~df['status'].isin(valid_statuses)]
            if not invalid_status.empty:
                issues.append(f"Orders with invalid status: {invalid_status['id'].tolist()}")
        
        return {'issues': issues, 'record_count': len(df)}
    
    def _validate_relationships(self, users_df: pd.DataFrame, 
                             products_df: pd.DataFrame, 
                             orders_df: pd.DataFrame) -> Dict[str, List[str]]:
        issues = []
        
        # Foreign key validation: orders.user_id -> users.id
        if 'user_id' in orders_df.columns and 'id' in users_df.columns:
            orphaned_orders = orders_df[~orders_df['user_id'].isin(users_df['id'])]
            if not orphaned_orders.empty:
                issues.append(f"Orders with invalid user_id: {orphaned_orders['id'].tolist()}")
        
        return {'issues': issues}
    
    def _validate_business_rules(self, users_df: pd.DataFrame, 
                               products_df: pd.DataFrame, 
                               orders_df: pd.DataFrame) -> Dict[str, List[str]]:
        issues = []
        
        # Business rule: Premium customers should have higher order values
        if 'customerType' in users_df.columns and 'user_id' in orders_df.columns:
            premium_users = users_df[users_df['customerType'] == 'premium']['id']
            premium_orders = orders_df[orders_df['user_id'].isin(premium_users)]
            
            if not premium_orders.empty:
                avg_premium_order = premium_orders['total'].mean()
                avg_regular_order = orders_df[~orders_df['user_id'].isin(premium_users)]['total'].mean()
                
                if avg_premium_order <= avg_regular_order:
                    issues.append("Premium customers don't have higher average order values")
        
        return {'issues': issues}

# Usage example
validator = TestDataValidator()

# Sample data (would be loaded from generated files)
users_data = pd.DataFrame([
    {'id': 1, 'email': 'john@test.com', 'firstName': 'John', 'lastName': 'Doe', 'customerType': 'premium'},
    {'id': 2, 'email': 'invalid-email', 'firstName': 'Jane', 'lastName': 'Smith', 'customerType': 'regular'}
])

products_data = pd.DataFrame([
    {'id': 1, 'name': 'Product 1', 'price': 99.99, 'inventory': 10},
    {'id': 2, 'name': 'Product 2', 'price': -5.00, 'inventory': 0}
])

orders_data = pd.DataFrame([
    {'id': 1, 'user_id': 1, 'total': 199.99, 'status': 'delivered'},
    {'id': 2, 'user_id': 999, 'total': 50.00, 'status': 'invalid_status'}
])

results = validator.validate_ecommerce_dataset(users_data, products_data, orders_data)

# Print validation results
for category, result in results.items():
    print(f"\n{category.upper()} VALIDATION:")
    if 'issues' in result:
        for issue in result['issues']:
            print(f"  ❌ {issue}")
    if 'record_count' in result:
        print(f"  📊 Records processed: {result['record_count']}")
"""
```

---

## Session 4: Advanced AI in Test Automation

### 4.1. Automating UI & API Tests with AI

#### Lý thuyết (45 phút)

**AI-Assisted Test Automation Benefits:**
- Faster script generation
- Better element locator strategies
- Automatic test maintenance
- Enhanced error handling
- Cross-browser compatibility

**Integration Patterns:**
1. **AI-Generated Scripts:** Complete test automation from requirements
2. **AI-Enhanced Scripts:** Improve existing automation
3. **AI-Maintained Scripts:** Self-healing tests
4. **AI-Optimized Scripts:** Performance and reliability improvements

**Tools Integration:**
- **Playwright + AI:** Modern browser automation
- **Selenium + AI:** Traditional web testing
- **REST Assured + AI:** API testing
- **Postman + AI:** API collection generation

#### Thực hành (75 phút)

**Lab 1: Complete UI Automation Generation**

```python
# Comprehensive UI test generation prompt
ui_automation_prompt = """
Generate a complete Playwright test automation suite for an e-commerce login flow:

REQUIREMENTS:
1. Login page with email/password fields
2. Success redirect to dashboard
3. Error handling for invalid credentials
4. Remember me functionality
5. Forgot password link
6. Social login buttons (Google, Facebook)

TECHNICAL REQUIREMENTS:
- Use Page Object Model pattern
- Include data-driven testing
- Add proper waits and assertions
- Handle different screen sizes
- Include accessibility testing
- Add performance checks (page load time)

GENERATE:
1. Page Object classes (LoginPage, DashboardPage)
2. Test data management
3. Test specifications with multiple scenarios
4. Configuration files
5. CI/CD integration setup

BEST PRACTICES:
- Use meaningful test names
- Include detailed comments
- Add error recovery
- Implement proper teardown
- Use environment-specific configurations
"""

# Expected sophisticated output
advanced_playwright_example = """
# pages/base_page.py
from playwright.async_api import Page
import asyncio
from typing import Optional

class BasePage:
    def __init__(self, page: Page):
        self.page = page
        self.timeout = 30000
    
    async def wait_for_load_state(self, state: str = "networkidle"):
        await self.page.wait_for_load_state(state)
    
    async def take_screenshot(self, name: str):
        await self.page.screenshot(path=f"screenshots/{name}.png")
    
    async def check_accessibility(self):
        # Inject axe-core for accessibility testing
        await self.page.add_script_tag(url="https://unpkg.com/axe-core@4.7.0/axe.min.js")
        results = await self.page.evaluate("() => axe.run()")
        return results

# pages/login_page.py
from .base_page import BasePage
from playwright.async_api import expect

class LoginPage(BasePage):
    def __init__(self, page):
        super().__init__(page)
        # Robust locator strategies
        self.email_input = page.get_by_test_id("email-input")
        self.password_input = page.get_by_test_id("password-input")
        self.login_button = page.get_by_role("button", name="Sign In")
        self.remember_me_checkbox = page.get_by_test_id("remember-me")
        self.forgot_password_link = page.get_by_role("link", name="Forgot Password?")
        self.error_message = page.get_by_test_id("error-message")
        self.google_login_button = page.get_by_test_id("google-login")
        self.facebook_login_button = page.get_by_test_id("facebook-login")
    
    async def navigate(self):
        await self.page.goto("/login")
        await self.wait_for_load_state()
    
    async def login(self, email: str, password: str, remember_me: bool = False):
        await self.email_input.fill(email)
        await self.password_input.fill(password)
        
        if remember_me:
            await self.remember_me_checkbox.check()
        
        # Measure login performance
        start_time = self.page.clock.now()
        await self.login_button.click()
        
        # Wait for navigation or error
        try:
            await self.page.wait_for_url("**/dashboard", timeout=5000)
            end_time = self.page.clock.now()
            return {"success": True, "duration": end_time - start_time}
        except:
            # Check for error message
            await expect(self.error_message).to_be_visible()
            return {"success": False, "error": await self.error_message.text_content()}
    
    async def validate_form_fields(self):
        # Comprehensive form validation
        validations = {}
        
        # Check if fields are visible and enabled
        validations['email_visible'] = await self.email_input.is_visible()
        validations['password_visible'] = await self.password_input.is_visible()
        validations['login_button_enabled'] = await self.login_button.is_enabled()
        
        # Check placeholder text
        validations['email_placeholder'] = await self.email_input.get_attribute("placeholder")
        
        # Check form validation attributes
        validations['email_required'] = await self.email_input.get_attribute("required") is not None
        validations['password_required'] = await self.password_input.get_attribute("required") is not None
        
        return validations

# tests/test_login.py
import pytest
from pages.login_page import LoginPage
from pages.dashboard_page import DashboardPage
from test_data.users import TestUsers
from playwright.async_api import expect

class TestLogin:
    
    @pytest.mark.asyncio
    async def test_successful_login(self, page, test_users):
        login_page = LoginPage(page)
        dashboard_page = DashboardPage(page)
        
        await login_page.navigate()
        
        # Validate page loaded correctly
        form_validations = await login_page.validate_form_fields()
        assert form_validations['email_visible']
        assert form_validations['password_visible']
        assert form_validations['login_button_enabled']
        
        # Perform login
        valid_user = test_users['valid_user']
        result = await login_page.login(valid_user['email'], valid_user['password'])
        
        assert result['success']
        assert result['duration'] < 3000  # Performance check: login < 3s
        
        # Verify dashboard elements
        await expect(dashboard_page.welcome_message).to_contain_text(valid_user['name'])
        await expect(dashboard_page.logout_button).to_be_visible()
    
    @pytest.mark.asyncio
    async def test_invalid_credentials(self, page, test_users):
        login_page = LoginPage(page)
        
        await login_page.navigate()
        
        invalid_user = test_users['invalid_user']
        result = await login_page.login(invalid_user['email'], invalid_user['password'])
        
        assert not result['success']
        assert 'Invalid credentials' in result['error']
        
        # Verify user stays on login page
        await expect(page).to_have_url("**/login")
    
    @pytest.mark.asyncio
    @pytest.mark.parametrize("email,password,expected_error", [
        ("", "password123", "Email is required"),
        ("invalid-email", "password123", "Please enter a valid email"),
        ("user@test.com", "", "Password is required"),
        ("user@test.com", "123", "Password must be at least 8 characters")
    ])
    async def test_form_validation(self, page, email, password, expected_error):
        login_page = LoginPage(page)
        await login_page.navigate()
        
        await login_page.email_input.fill(email)
        await login_page.password_input.fill(password)
        await login_page.login_button.click()
        
        await expect(login_page.error_message).to_contain_text(expected_error)
    
    @pytest.mark.asyncio
    async def test_remember_me_functionality(self, page, test_users):
        login_page = LoginPage(page)
        
        await login_page.navigate()
        
        valid_user = test_users['valid_user']
        await login_page.login(valid_user['email'], valid_user['password'], remember_me=True)
        
        # Close browser and reopen (simulate)
        await page.context.close()
        new_context = await page.context.browser.new_context()
        new_page = await new_context.new_page()
        
        # Navigate to protected page - should not redirect to login
        await new_page.goto("/dashboard")
        await expect(new_page).to_have_url("**/dashboard")
    
    @pytest.mark.accessibility
    @pytest.mark.asyncio
    async def test_login_accessibility(self, page):
        login_page = LoginPage(page)
        await login_page.navigate()
        
        # Run accessibility audit
        accessibility_results = await login_page.check_accessibility()
        
        # Should have no violations
        violations = accessibility_results.get('violations', [])
        assert len(violations) == 0, f"Accessibility violations found: {violations}"
    
    @pytest.mark.mobile
    @pytest.mark.asyncio
    async def test_mobile_responsive_login(self, mobile_page, test_users):
        login_page = LoginPage(mobile_page)
        await login_page.navigate()
        
        # Check mobile-specific elements
        await expect(login_page.email_input).to_be_visible()
        await expect(login_page.password_input).to_be_visible()
        
        # Verify touch-friendly button size
        login_button_box = await login_page.login_button.bounding_box()
        assert login_button_box['height'] >= 44  # iOS minimum touch target
        
        # Test mobile login flow
        valid_user = test_users['valid_user']
        result = await login_page.login(valid_user['email'], valid_user['password'])
        assert result['success']

# test_data/users.py
class TestUsers:
    @staticmethod
    def get_test_users():
        return {
            'valid_user': {
                'email': 'john.doe@example.com',
                'password': 'SecurePass123!',
                'name': 'John Doe'
            },
            'invalid_user': {
                'email': 'invalid@example.com',
                'password': 'wrongpassword'
            },
            'premium_user': {
                'email': 'premium@example.com',
                'password': 'PremiumPass456!',
                'name': 'Premium User',
                'type': 'premium'
            }
        }

# conftest.py
import pytest
from playwright.async_api import async_playwright
from test_data.users import TestUsers

@pytest.fixture(scope="session")
async def browser():
    p = await async_playwright().start()
    browser = await p.chromium.launch(headless=False)
    yield browser
    await browser.close()
    await p.stop()

@pytest.fixture
async def page(browser):
    context = await browser.new_context(
        viewport={'width': 1280, 'height': 720},
        record_video_dir="videos/"
    )
    page = await context.new_page()
    yield page
    await context.close()

@pytest.fixture
async def mobile_page(browser):
    context = await browser.new_context(
        **playwright.devices['iPhone 12'],
        record_video_dir="videos/"
    )
    page = await context.new_page()
    yield page
    await context.close()

@pytest.fixture
def test_users():
    return TestUsers.get_test_users()

# playwright.config.js
module.exports = {
    testDir: './tests',
    timeout: 30000,
    expect: {
        timeout: 5000,
    },
    fullyParallel: true,
    forbidOnly: !!process.env.CI,
    retries: process.env.CI ? 2 : 0,
    workers: process.env.CI ? 1 : undefined,
    reporter: [
        ['html'],
        ['junit', { outputFile: 'results.xml' }],
        ['json', { outputFile: 'results.json' }]
    ],
    use: {
        baseURL: process.env.BASE_URL || 'http://localhost:3000',
        trace: 'on-first-retry',
        screenshot: 'only-on-failure',
        video: 'retain-on-failure',
    },
    projects: [
        {
            name: 'chromium',
            use: { ...devices['Desktop Chrome'] },
        },
        {
            name: 'firefox',
            use: { ...devices['Desktop Firefox'] },
        },
        {
            name: 'webkit',
            use: { ...devices['Desktop Safari'] },
        },
        {
            name: 'mobile-chrome',
            use: { ...devices['Pixel 5'] },
        },
    ],
};
"""
```

**Lab 2: API Test Automation**

```python
# Comprehensive API test generation
api_automation_prompt = """
Generate complete API test automation for an e-commerce REST API:

ENDPOINTS TO TEST:
1. POST /api/auth/login - User authentication
2. GET /api/users/profile - Get user profile
3. GET /api/products - List products with pagination
4. POST /api/orders - Create new order
5. GET /api/orders/{id} - Get order details
6. PUT /api/orders/{id}/status - Update order status

REQUIREMENTS:
- Authentication handling (JWT tokens)
- Data-driven testing with multiple test cases
- Error handling and negative scenarios
- Performance testing (response times)
- Contract testing (schema validation)
- Environment configuration (dev, staging, prod)

GENERATE:
1. API client classes
2. Test data management
3. Comprehensive test suites
4. Utilities for common operations
5. Reporting and logging
"""

# Advanced API testing implementation
api_testing_example = """
# api_client/base_client.py
import requests
import json
from typing import Dict, Any, Optional
import time
import logging

class APIClient:
    def __init__(self, base_url: str, timeout: int = 30):
        self.base_url = base_url.rstrip('/')
        self.timeout = timeout
        self.session = requests.Session()
        self.logger = logging.getLogger(__name__)
        
    def _make_request(self, method: str, endpoint: str, **kwargs) -> Dict[str, Any]:
        url = f"{self.base_url}{endpoint}"
        
        # Add default headers
        headers = kwargs.get('headers', {})
        headers.setdefault('Content-Type', 'application/json')
        kwargs['headers'] = headers
        
        # Performance tracking
        start_time = time.time()
        
        try:
            response = self.session.request(
                method=method,
                url=url,
                timeout=self.timeout,
                **kwargs
            )
            
            end_time = time.time()
            duration = (end_time - start_time) * 1000  # Convert to milliseconds
            
            # Log request details
            self.logger.info(f"{method} {url} - {response.status_code} - {duration:.2f}ms")
            
            return {
                'status_code': response.status_code,
                'headers': dict(response.headers),
                'body': response.json() if response.text else None,
                'response_time': duration,
                'raw_response': response
            }
            
        except requests.exceptions.RequestException as e:
            self.logger.error(f"Request failed: {e}")
            raise
    
    def get(self, endpoint: str, **kwargs) -> Dict[str, Any]:
        return self._make_request('GET', endpoint, **kwargs)
    
    def post(self, endpoint: str, data: Any = None, **kwargs) -> Dict[str, Any]:
        if data:
            kwargs['json'] = data
        return self._make_request('POST', endpoint, **kwargs)
    
    def put(self, endpoint: str, data: Any = None, **kwargs) -> Dict[str, Any]:
        if data:
            kwargs['json'] = data
        return self._make_request('PUT', endpoint, **kwargs)
    
    def delete(self, endpoint: str, **kwargs) -> Dict[str, Any]:
        return self._make_request('DELETE', endpoint, **kwargs)

# api_client/auth_client.py
from .base_client import APIClient
from typing import Optional

class AuthClient(APIClient):
    def __init__(self, base_url: str):
        super().__init__(base_url)
        self.access_token: Optional[str] = None
        self.refresh_token: Optional[str] = None
    
    def login(self, email: str, password: str) -> Dict[str, Any]:
        response = self.post('/api/auth/login', {
            'email': email,
            'password': password
        })
        
        if response['status_code'] == 200:
            self.access_token = response['body']['access_token']
            self.refresh_token = response['body'].get('refresh_token')
            
            # Set auth header for future requests
            self.session.headers['Authorization'] = f"Bearer {self.access_token}"
        
        return response
    
    def logout(self) -> Dict[str, Any]:
        response = self.post('/api/auth/logout')
        
        if response['status_code'] == 200:
            self.access_token = None
            self.refresh_token = None
            del self.session.headers['Authorization']
        
        return response
    
    def refresh_access_token(self) -> Dict[str, Any]:
        if not self.refresh_token:
            raise ValueError("No refresh token available")
        
        response = self.post('/api/auth/refresh', {
            'refresh_token': self.refresh_token
        })
        
        if response['status_code'] == 200:
            self.access_token = response['body']['access_token']
            self.session.headers['Authorization'] = f"Bearer {self.access_token}"
        
        return response

# tests/api/test_auth_api.py
import pytest
from api_client.auth_client import AuthClient
from test_data.users import APITestUsers
import jsonschema

class TestAuthAPI:
    
    @pytest.fixture(autouse=True)
    def setup(self, api_base_url):
        self.client = AuthClient(api_base_url)
        self.test_users = APITestUsers()
    
    def test_successful_login(self):
        user = self.test_users.valid_user()
        
        response = self.client.login(user['email'], user['password'])
        
        # Status code validation
        assert response['status_code'] == 200
        
        # Response time validation
        assert response['response_time'] < 2000  # Less than 2 seconds
        
        # Schema validation
        expected_schema = {
            "type": "object",
            "properties": {
                "access_token": {"type": "string"},
                "refresh_token": {"type": "string"},
                "expires_in": {"type": "integer"},
                "user": {
                    "type": "object",
                    "properties": {
                        "id": {"type": "integer"},
                        "email": {"type": "string"},
                        "name": {"type": "string"}
                    },
                    "required": ["id", "email", "name"]
                }
            },
            "required": ["access_token", "user"]
        }
        
        jsonschema.validate(response['body'], expected_schema)
        
        # Business logic validation
        assert response['body']['user']['email'] == user['email']
        assert len(response['body']['access_token']) > 0
    
    @pytest.mark.parametrize("email,password,expected_status,expected_error", [
        ("invalid@test.com", "password123", 401, "Invalid credentials"),
        ("user@test.com", "wrongpassword", 401, "Invalid credentials"),  
        ("", "password123", 400, "Email is required"),
        ("user@test.com", "", 400, "Password is required"),
        ("not-an-email", "password123", 400, "Invalid email format")
    ])
    def test_login_validation_errors(self, email, password, expected_status, expected_error):
        response = self.client.login(email, password)
        
        assert response['status_code'] == expected_status
        assert expected_error in response['body']['error']
    
    def test_login_rate_limiting(self):
        user = self.test_users.invalid_user()
        
        # Make multiple failed login attempts
        for i in range(5):
            response = self.client.login(user['email'], user['password'])
            
            if i < 3:
                assert response['status_code'] == 401
            else:
                # Should be rate limited after 3 attempts
                assert response['status_code'] == 429
                assert "Too many attempts" in response['body']['error']
    
    def test_concurrent_login_sessions(self):
        user = self.test_users.valid_user()
        
        # Create multiple clients
        client1
        Generate detailed test cases for: {feature_description}
        Format: Given-When-Then
        Include: Positive, Negative, Edge cases
        """
        
        response = self.client.chat.completions.create(
            model="gpt-4",
            messages=[{"role": "user", "content": prompt}]
        )
        
        return response.choices[0].message.content

# Test the helper
helper = TestAIHelper("your-api-key")
test_cases = helper.generate_test_case("User login with email and password")
print(test_cases)
```

---

## Session 2: AI-Assisted Test Case Generation

### 2.1. Using Generative AI to Generate Test Cases

#### Lý thuyết (60 phút)

**Prompt Engineering cho Testing:**

**Cấu trúc Prompt hiệu quả:**
1. **Context:** Mô tả hệ thống/tính năng
2. **Task:** Yêu cầu cụ thể
3. **Format:** Định dạng mong muốn
4. **Constraints:** Ràng buộc/yêu cầu đặc biệt

```
Template:
"""
CONTEXT: [Mô tả hệ thống/tính năng]
TASK: Generate test cases for [specific functionality]
FORMAT: 
- Test Case ID
- Title
- Preconditions
- Steps
- Expected Results
CONSTRAINTS:
- Include positive, negative, and edge cases
- Focus on [specific aspects]
"""
```

**RAG (Retrieval-Augmented Generation):**
- Định nghĩa: Kết hợp thông tin từ database/documents với LLM
- Lợi ích: Giảm hallucination, tăng accuracy
- Ứng dụng: Sử dụng existing test cases, requirements documents

**RAG Architecture:**
```
Documents → Vector DB → Retrieval → LLM → Enhanced Output
```

#### Thực hành (90 phút)

**Lab 1: Basic Test Case Generation**

```python
# Prompt Templates
basic_prompt = """
Generate test cases for a login feature with the following requirements:
- Users can login with email/username and password
- System should validate credentials
- Failed attempts should be tracked
- Account locks after 3 failed attempts

Format each test case as:
ID: TC_XXX
Title: [Clear title]
Preconditions: [What needs to be ready]
Steps: [Numbered steps]
Expected: [Expected outcome]
"""

advanced_prompt = """
CONTEXT: E-commerce web application with user authentication
FEATURE: Login functionality
REQUIREMENTS:
- Support email and username login
- Password complexity validation
- Remember me option
- Social login (Google, Facebook)
- Account lockout policy
- Password reset flow

TASK: Generate comprehensive test cases covering:
1. Functional testing (positive flows)
2. Negative testing (invalid inputs)
3. Security testing (injection, brute force)
4. UI/UX testing (responsive, accessibility)
5. Integration testing (SSO, password reset)

FORMAT: Gherkin syntax (Given-When-Then)
CONSTRAINTS: 
- Minimum 15 test cases
- Cover all requirements
- Include data-driven scenarios
"""
```

**Lab 2: RAG Implementation**

```python
# Simple RAG for test case generation
import json
from typing import List

class TestCaseRAG:
    def __init__(self):
        self.knowledge_base = {
            "login_requirements": [
                "Email/username authentication",
                "Password complexity: min 8 chars, special chars",
                "Account lockout after 3 failed attempts",
                "Session timeout after 30 minutes"
            ],
            "existing_test_cases": [
                {
                    "id": "TC_001",
                    "title": "Valid login with email",
                    "steps": ["Enter valid email", "Enter valid password", "Click login"],
                    "expected": "User logged in successfully"
                }
            ],
            "common_test_patterns": [
                "Boundary value testing",
                "Equivalence partitioning",
                "State transition testing"
            ]
        }
    
    def retrieve_context(self, query: str) -> str:
        # Simple keyword matching (in real implementation, use vector search)
        context = []
        if "login" in query.lower():
            context.extend(self.knowledge_base["login_requirements"])
            context.extend([tc["title"] for tc in self.knowledge_base["existing_test_cases"]])
        
        return "\n".join(context)
    
    def generate_with_rag(self, feature_description: str) -> str:
        context = self.retrieve_context(feature_description)
        
        prompt = f"""
        CONTEXT INFORMATION:
        {context}
        
        TASK: Generate new test cases for: {feature_description}
        
        REQUIREMENTS:
        - Don't duplicate existing test cases
        - Follow established patterns
        - Consider all requirements mentioned in context
        
        FORMAT: Gherkin scenarios
        """
        
        # In real implementation, call OpenAI API here
        return prompt

# Usage
rag = TestCaseRAG()
enhanced_prompt = rag.generate_with_rag("Login functionality testing")
print(enhanced_prompt)
```

### 2.2. Refining AI-Generated Test Cases

#### Lý thuyết (45 phút)

**Phân tích chất lượng Test Cases:**

**Tiêu chí đánh giá:**
1. **Coverage:** Có đủ positive, negative, edge cases?
2. **Clarity:** Test steps có rõ ràng, dễ hiểu?
3. **Executability:** Có thể thực hiện được không?
4. **Traceability:** Link với requirements?
5. **Maintainability:** Dễ cập nhật khi cần?

**Common Issues với AI-generated test cases:**
- Thiếu context cụ thể của hệ thống
- Test data không realistic
- Missing edge cases
- Over-complicated scenarios
- Không follow testing standards

**Improvement Strategies:**
1. **Iterative Prompting:** Cải thiện dần qua nhiều lần
2. **Domain Knowledge Injection:** Bổ sung thông tin chuyên môn
3. **Template Standardization:** Sử dụng template chuẩn
4. **Human Review:** Kết hợp với kinh nghiệm tester

#### Thực hành (75 phút)

**Lab 1: Test Case Quality Analysis**

```python
# AI-generated test case example (deliberately flawed)
ai_generated = """
Test Case: Login Test
1. Go to login page
2. Enter username
3. Enter password
4. Click login
5. Verify login successful
"""

# Improvement process
improvement_prompt = """
Improve this test case with the following requirements:
- Add specific test data
- Include preconditions and postconditions
- Add negative scenarios
- Make steps more detailed
- Add expected results for each step

Original test case:
{ai_generated}

Business context:
- This is for a banking application
- Security is critical
- Users can login with account number or email
- 2FA is required for first-time devices
"""

improved_prompt = f"""
CONTEXT: Banking application login testing
ORIGINAL TEST CASE: {ai_generated}

IMPROVEMENTS NEEDED:
1. Add specific, realistic test data
2. Include security considerations
3. Add preconditions/postconditions
4. Create both positive and negative scenarios
5. Consider 2FA flow
6. Add validation points

REQUIREMENTS:
- Follow banking security standards
- Include accessibility testing
- Consider mobile responsiveness
- Add performance expectations

OUTPUT FORMAT:
Test Case ID: [Unique ID]
Title: [Descriptive title]
Priority: [High/Medium/Low]
Preconditions: [Setup requirements]
Test Data: [Specific data to use]
Steps: [Detailed numbered steps]
Expected Results: [Clear expected outcomes]
Postconditions: [Cleanup requirements]
"""
```

**Lab 2: Domain Knowledge Enhancement**

```python
# Domain-specific enhancement
banking_context = """
BANKING DOMAIN KNOWLEDGE:
- Account numbers: 10-12 digits
- Password policy: 8-16 chars, uppercase, lowercase, numbers, special chars
- Session timeout: 15 minutes of inactivity
- Login attempts: Max 3 before account lock
- 2FA: SMS OTP or authenticator app
- Regulatory compliance: PCI DSS, SOX
- Audit trail: All login attempts logged

COMMON BANKING TEST SCENARIOS:
- Joint account access
- Corporate account delegation
- International character support
- Accessibility compliance (WCAG 2.1)
- Browser compatibility
- Network interruption handling
"""

enhanced_prompt = f"""
{banking_context}

Generate banking-specific login test cases considering:
1. Regulatory compliance requirements
2. Security best practices
3. Accessibility standards
4. Multi-device scenarios
5. Edge cases specific to banking

Focus on scenarios that are unique to banking domain.
"""
```

### 2.3. Automation Readiness of AI-Generated Test Cases

#### Lý thuyết (30 phút)

**Converting Test Cases to Automation:**

**Automation Readiness Checklist:**
- [ ] Test steps are specific and unambiguous
- [ ] Test data is clearly defined
- [ ] UI elements are identifiable
- [ ] Expected results are verifiable
- [ ] Dependencies are minimal

**Automation Patterns:**
1. **Page Object Model:** Organize UI interactions
2. **Data-Driven Testing:** Parameterize test data
3. **Behavior-Driven Development:** Gherkin scenarios
4. **API Testing:** REST/GraphQL test patterns

#### Thực hành (90 phút)

**Lab 1: Test Case to Playwright Conversion**

```python
# Original AI-generated test case
test_case = """
Test Case: User Login
Given user is on login page
When user enters valid email "user@test.com"
And user enters valid password "Test123!"
And user clicks login button
Then user should be redirected to dashboard
And welcome message should display user's name
"""

# AI prompt for Playwright conversion
conversion_prompt = f"""
Convert this test case to Playwright automation code:

{test_case}

Requirements:
- Use Page Object Model pattern
- Include proper waits and assertions
- Add error handling
- Use data-driven approach
- Follow Playwright best practices

Generate:
1. Page Object class
2. Test specification
3. Test data file
"""

# Expected output structure:
playwright_structure = """
# pages/login_page.py
class LoginPage:
    def __init__(self, page):
        self.page = page
        self.email_input = page.locator('[data-testid="email"]')
        self.password_input = page.locator('[data-testid="password"]')
        self.login_button = page.locator('[data-testid="login-btn"]')
    
    async def login(self, email, password):
        await self.email_input.fill(email)
        await self.password_input.fill(password)
        await self.login_button.click()

# tests/test_login.py
import pytest
from pages.login_page import LoginPage
from pages.dashboard_page import DashboardPage

@pytest.mark.asyncio
async def test_valid_login(page, test_data):
    login_page = LoginPage(page)
    dashboard_page = DashboardPage(page)
    
    await page.goto("/login")
    await login_page.login(test_data["email"], test_data["password"])
    
    await expect(page).to_have_url("/dashboard")
    await expect(dashboard_page.welcome_message).to_contain_text(test_data["expected_name"])

# test_data.json
{
    "valid_user": {
        "email": "user@test.com",
        "password": "Test123!",
        "expected_name": "John Doe"
    }
}
"""
```

**Lab 2: API Test Generation**

```python
# AI prompt for API test generation
api_test_prompt = """
Generate API test cases for login endpoint:

ENDPOINT: POST /api/auth/login
REQUEST BODY:
{
    "email": "string",
    "password": "string",
    "remember_me": "boolean"
}

RESPONSES:
200: {"token": "jwt_token", "user": {...}}
400: {"error": "Invalid credentials"}
429: {"error": "Too many attempts"}

Generate:
1. Postman collection
2. Python requests test
3. Playwright API test
4. Test data variations

Include:
- Happy path scenarios
- Error handling
- Security testing
- Performance considerations
"""

# Expected API test structure
api_test_example = """
# tests/api/test_auth.py
import pytest
import requests
from playwright.sync_api import APIRequestContext

class TestAuthAPI:
    base_url = "https://api.example.com"
    
    def test_valid_login_requests(self):
        url = f"{self.base_url}/api/auth/login"
        payload = {
            "email": "valid@test.com",
            "password": "ValidPass123!"
        }
        
        response = requests.post(url, json=payload)
        
        assert response.status_code == 200
        assert "token" in response.json()
        assert response.json()["user"]["email"] == payload["email"]
    
    @pytest.mark.asyncio
    async def test_invalid_login_playwright(self, api_context: APIRequestContext):
        response = await api_context.post(f"{self.base_url}/api/auth/login", data={
            "email": "invalid@test.com",
            "password": "wrong_password"
        })
        
        assert response.status == 400
        body = await response.json()
        assert "error" in body
"""
```

---

## Session 3: AI-Powered Test Data Generation

### 3.1. Introduction to AI-Driven Test Data Creation

#### Lý thuyết (45 phút)

**Tại sao Test Data quan trọng:**
- Chiếm 30-40% effort trong testing
- Ảnh hưởng trực tiếp đến test coverage
- Quyết định chất lượng của test execution
- Critical cho performance và security testing

**Challenges với Traditional Data Generation:**
- Time-consuming manual creation
- Limited variety and edge cases
- Privacy concerns with production data
- Maintenance overhead
- Consistency across environments

**AI Advantages:**
- Generate large volumes quickly
- Create realistic, diverse data
- Handle complex relationships
- Generate edge cases automatically
- Maintain data privacy

**Types of Test Data:**
1. **Master Data:** Users, products, categories
2. **Transactional Data:** Orders, payments, logs
3. **Reference Data:** Countries, currencies, codes
4. **Configuration Data:** Settings, parameters

#### Thực hành (45 phút)

**Lab 1: Basic Data Generation**

```python
# Simple user data generation prompt
user_data_prompt = """
Generate 10 realistic user profiles for testing an e-commerce application.

Requirements:
- Diverse demographics (age, location, occupation)
- Realistic names from different cultures
- Valid email formats
- Phone numbers in US format
- Mix of customer types (new, returning, premium)

Format: JSON array with fields:
- id, firstName, lastName, email, phone, dateOfBirth, address, customerType, registrationDate

Ensure data looks realistic and could pass basic validation.
"""

# Advanced data generation with relationships
complex_data_prompt = """
Generate a complete e-commerce test dataset including:

USERS (5 users):
- Personal information
- Address details
- Payment methods
- Order history

PRODUCTS (20 products):
- Different categories
- Price ranges
- Inventory levels
- Ratings and reviews

ORDERS (15 orders):
- Link to existing users
- Multiple products per order
- Different order statuses
- Realistic timestamps

Requirements:
- Maintain referential integrity
- Include edge cases (empty cart, high-value orders)
- Mix of payment methods
- Various shipping addresses
- Realistic product names and descriptions

Output: Separate JSON files for each entity type
"""
```

### 3.2. Generating Test Data with Generative AI

#### Lý thuyết (30 phút)

**Schema-Driven Generation:**
- OpenAPI/Swagger specifications
- Database schemas (SQL DDL)
- JSON Schema validation
- XML Schema (XSD)

**Data Formats:**
- **JSON:** API testing, NoSQL databases
- **CSV:** Bulk imports, Excel integration
- **XML:** Legacy systems, configuration files
- **SQL:** Database seeding

**Advanced Techniques:**
- **Constraint satisfaction:** Business rules compliance
- **Relationship modeling:** Foreign key integrity
- **Temporal data:** Time-series, historical data
- **Localization:** Multi-language, regional formats

#### Thực hành (90 phút)

**Lab 1: Schema-Based Generation**

```python
# OpenAPI schema example
openapi_schema = """
User:
  type: object
  required:
    - id
    - email
    - firstName
    - lastName
  properties:
    id:
      type: integer
      minimum: 1
    email:
      type: string
      format: email
    firstName:
      type: string
      minLength: 1
      maxLength: 50
    lastName:
      type: string
      minLength: 1
      maxLength: 50
    dateOfBirth:
      type: string
      format: date
    phoneNumber:
      type: string
      pattern: '^\\+?[1-9]\\d{1,14}$'
    address:
      $ref: '#/components/schemas/Address'

Address:
  type: object
  properties:
    street:
      type: string
    city:
      type: string
    state:
      type: string
    zipCode:
      type: string
      pattern: '^\\d{5}(-\\d{4})?$'
    country:
      type: string
      enum: ['US', 'CA', 'UK', 'DE', 'FR']
"""

schema_prompt = f"""
Based on this OpenAPI schema:

{openapi_schema}

Generate 20 valid user records that:
1. Comply with all schema constraints
2. Include realistic, diverse data
3. Cover edge cases for validation testing
4. Include some boundary values (min/max lengths)
5. Represent different countries and formats

Output format: JSON array
Include comments explaining the test strategy for each edge case.
"""

# SQL Schema example
sql_schema = """
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100) NOT NULL,
    last_name VARCHAR(100) NOT NULL,
    date_of_birth DATE,
    phone_number VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    is_active BOOLEAN DEFAULT true,
    user_type ENUM('customer', 'admin', 'moderator') DEFAULT 'customer'
);

CREATE TABLE orders (
    id SERIAL PRIMARY KEY,
    user_id INTEGER REFERENCES users(id),
    order_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    total_amount DECIMAL(10,2) NOT NULL,
    status ENUM('pending', 'confirmed', 'shipped', 'delivered', 'cancelled'),
    shipping_address TEXT,
    billing_address TEXT
);
"""

sql_data_prompt = f"""
Generate SQL INSERT statements for the following schema:

{sql_schema}

Requirements:
- 15 users with diverse profiles
- 25 orders distributed across users
- Realistic data that follows business logic
- Include various order statuses
- Some users with multiple orders, some with none
- Test boundary conditions (very old/young users, high-value orders)

Output:
1. INSERT statements for users table
2. INSERT statements for orders table
3. Comments explaining the test scenarios covered
"""
```

**Lab 2: Complex Relationship Data**

```python
# E-commerce complete dataset generation
ecommerce_prompt = """
Generate a complete e-commerce test dataset with the following entities and relationships:

USERS (10 records):
- Mix of customer types: new (2), regular (6), premium (2)
- Age distribution: 18-25 (3), 26-40 (4), 41-65 (3)
- Geographic distribution: US (6), Canada (2), UK (2)

CATEGORIES (5 categories):
- Electronics, Clothing, Books, Home & Garden, Sports

PRODUCTS (25 products):
- 5 products per category
- Price range: $10-$500
- Mix of in-stock and out-of-stock items
- Include product variants (size, color) where applicable

ORDERS (20 orders):
- Distributed across 8 users (2 users with no orders)
- Order values: $20-$800
- Status distribution: 50% delivered, 30% shipped, 15% pending, 5% cancelled
- Include multi-item orders and single-item orders

BUSINESS RULES:
- Premium customers get 10% discount
- Free shipping over $100
- Can't order out-of-stock items
- Order total must match item prices + tax - discounts

OUTPUT FORMAT:
Separate JSON files for each entity, with clear relationship keys.
Include a summary of test scenarios this data enables.
"""
```

### 3.3. Transforming and Validating Test Data

#### Lý thuyết (30 phút)

**Data Transformation Needs:**
- Format conversion (JSON ↔ CSV ↔ XML)
- Schema evolution (adding/removing fields)
- Data cleansing (removing duplicates, fixing formats)
- Anonymization (PII masking)

**Validation Strategies:**
- Schema validation
- Business rule validation
- Data quality checks
- Referential integrity

**Tools and Libraries:**
- **Pandas:** Data manipulation and analysis
- **Faker:** Realistic fake data generation
- **JSONSchema:** JSON validation
- **Pydantic:** Data modeling and validation

#### Thực hành (60 phút)

**Lab 1: Data Format Conversion**

```python
# AI prompt for data transformation
transformation_prompt = """
Convert this JSON user data to CSV format, then create SQL INSERT statements:

JSON Data:
[
    {
        "id": 1,
        "name": "John Doe",
        "email": "john@example.com",
        "address": {
            "street": "123 Main St",
            "city": "Anytown",
            "state": "CA",
            "zip": "12345"
        },
        "orders": [
            {"id": 101, "total": 99.99, "date": "2024-01-15"},
            {"id": 102, "total": 149.50, "date": "2024-02-01"}
        ]
    }
]

Requirements:
1. Flatten nested objects for CSV
2. Handle arrays (orders) appropriately
3. Generate SQL for normalized tables (users, addresses, orders)
4. Maintain referential integrity
5. Include proper data types in SQL

Output:
1. CSV format
2. SQL CREATE TABLE statements
3. SQL INSERT statements
"""

# Python validation script
validation_script = """
import json
import pandas as pd
from jsonschema import validate, ValidationError
from typing import List, Dict

def validate_user_data(data: List[Dict]) -> Dict[str, List[str]]:
    '''Validate generated user data for common issues'''
    
    issues = {
        'email_format': [],
        'duplicate_emails': [],
        'missing_required': [],
        'invalid_dates': [],
        'business_rules': []
    }
    
    emails_seen = set()
    
    for i, user in enumerate(data):
        # Check required fields
        required = ['id', 'email', 'firstName', 'lastName']
        missing = [field for field in required if field not in user or not user[field]]
        if missing:
            issues['missing_required'].append(f"User {i}: Missing {missing}")
        
        # Check email format
        email = user.get('email', '')
        if email and '@' not in email:
            issues['email_format'].append(f"User {i}: Invalid email format")
        
        # Check for duplicates
        if email in emails_seen:
            issues['duplicate_emails'].append(f"User {i}: Duplicate email {email}")
        emails_seen.add(email)
        
        # Business rule: Premium customers should have order history
        if user.get('customerType') == 'premium' and not user.get('orders'):
            issues['business_rules'].append(f"User