# 环卫基础数据推送的后端服务
环卫全周期系统后端服务应用，使用Node.js、Yoga-GraphQL、PostgreSQL和Prisma构建的可靠API，用于管理与环卫相关的数据。该项目提供了各种查询和修改，以实现高效的数据处理。

## 目录

- [特征](#特征)
- [使用的技术](#使用的技术)
- [用法](#用法)

## 特征

- GraphQL API 提供灵活的数据获取，与传统 REST API 不同，GraphQL 通过单一的端点处理所有请求，简化了 API 的管理和使用。支持订阅功能，允许客户端实时接收数据更新。
- 支持增删改查来管理数据。
- 与 Prisma 集成以进行数据库管理。
- 使用 TypeScript 构建，以实现类型安全并增强开发体验。

## 使用的技术

- **Node.js**
- **Yoga-GraphQL**
- **Prisma**
- **Type-GraphQL**
- **TypeScript**
- **Express.js**
- **Neon PostgreSQL**

## 用法
1. 设置环境变量。在根目录中创建一个 .env 文件并添加数据库连接字符串和其他必要的配置：
   
   ```bash
   DATABASE_URL = your_database_url
   PORT = your_port_here (default 4000)
   EMAIL_USER = your_smtp_user_email_here
   EMAIL_PASS = your_smtp_user_password_here
   JWT_SECRET = your_jwt_secret_here
   
2. 运行以下命令从 prisma 模式生成 typegraphQL 类型：
   
   ```bash
   npx prisma generate

### 启动服务器
  
      npm run dev
  
 
## 测试增删改查示例
要测试 GraphQL API，请按照以下步骤操作：
    - 访问 GraphQL API：打开浏览器并导航至http://localhost:${PORT}>/graphql。
    - 使用 GraphQL Playground：您可以使用内置的 GraphQL Playground 来测试增删改查。
  

### 身份验证和用户管理

  #### 注册新用户

    mutation {
      register(userData: {
        name: "Eric"
        email: "johnhomepageinc@gmail.com
        password: "securepassword"
      }) {
        id
        name
        email
        isVerified
      }
    }

#### 登录

    mutation {
      login(email: "johnhomepageinc@gmail.com, password: "securepassword") {
        token
      }
    }

#### 发送 OTP

    mutation {
      resendOtp(email: "johnhomepageinc@gmail.com")
    }

#### 通过电子邮件删除用户

    mutation {
      deleteUserByEmail(email: "johnhomepageinc@gmail.com") {
        id
        name
        email
      }
    }

#### 使用 OTP 验证用户（通过电子邮件收到 OTP 后）

    mutation {
      login(email: "johnhomepageinc@gmail.com", password: "securepassword", otp: "123456") {
        token
      }
    }


#### 更新用户个人资料

    mutation {
      updateProfile(email: "johnhomepageinc@gmail.com", userData: {
        name: "John Updated"
        phone: "9876543210"
        address: "广东省深圳市福田区"
        password: "newpassword123"
      }) {
        id
        name
        email
        phone
        address
        isVerified
      }
    }


#### 通过电子邮件删除用户
    mutation {
      deleteUserByEmail(email: "johnhomepageinc@gmail.com") {
        id
        name
        email
      }
    }

#### 通过向用户的电子邮件发送 OTP 来请求重置密码
    mutation {
      forgotPassword(email: "user@example.com")
    }

#### 使用收到的 OTP 重置密码
    mutation {
      resetPassword(
        email: "user@example.com",
        otp: "123456",  # Replace with the OTP sent to the email
        newPassword: "newSecurePassword123"
      )
    }


### 车辆管理
#### 获取所有车辆
    query {
      categoriesCar {
        guid
        sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight
      }
    }

#### 单个车辆查找
    query {
      categoriesCar {
        guid
        sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight
      }{
        guid
       sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight
      }
    }

#### 添加车辆
    mutation {
      createCategoryCar( 
        sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight) {
        guid
       sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight
      }
    }

  #### 修改车辆
    mutation {
      createCategoryCar( 
        sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight) {
        guid
       sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight
      }
    }


#### 按guid删除车辆
    mutation {
      deleteCategory(guid: "123e4567-e89b-12d3-a456-426614174000") {
         guid
       sectionId
        carNumber
        engineNumber
        dynamicType
        ownershipType
        status
        acquisitionDate
        operationalDate
        annualInspectionDate
        drivingLicenseRegistrationDate
        affiliatedEnterprise
        carLicenseColor
        carLength
        carWidth
        carHeight
      }
    }

###  人员管理
#### 获取所有人员
    query {
      categoriesPerson {
        guid
        personCode
        personName
        gender
        idNumber
        birthdate
        education
        age
        residentialAddress
        emergencyContact
        emergencyContactNumber
        specialCaseDescription
        SubordinateCompany
        owningLot
        deviceNumber
        socialSecurityNumber
        remark
      }
    }

#### 单个人员查找
    query {
      (guid: 1) {
        guid
        personCode
        personName
        gender
        idNumber
        birthdate
        education
        age
        residentialAddress
        emergencyContact
        emergencyContactNumber
        specialCaseDescription
        SubordinateCompany
        owningLot
        deviceNumber
        socialSecurityNumber
        remark
      }
    }


#### 人员update
    mutation {
      createPerson(
        personCode
        personName
        gender
        idNumber
        birthdate
        education
        age
        residentialAddress
        emergencyContact
        emergencyContactNumber
        specialCaseDescription
        SubordinateCompany
        owningLot
        deviceNumber
        socialSecurityNumber
        remark
      ) {
        guid
        personCode
        personName
        gender
        idNumber
        birthdate
        education
        age
        residentialAddress
        emergencyContact
        emergencyContactNumber
        specialCaseDescription
        SubordinateCompany
        owningLot
        deviceNumber
        socialSecurityNumber
        remark
      }
    }

#### 删除人员
    mutation {
      deletePerson(guid: "123e4567-e89b-12d3-a456-426614174000") {
       guid
        personCode
        personName
        gender
        idNumber
        birthdate
        education
        age
        residentialAddress
        emergencyContact
        emergencyContactNumber
        specialCaseDescription
        SubordinateCompany
        owningLot
        deviceNumber
        socialSecurityNumber
        remark
      }
    }

### 标段管理
### 企业管理
### 合同管理
### 公厕管理
### 焚烧厂管理
### 分类源头管理
