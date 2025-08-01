# 测试说明

本目录包含 `lrh-eslint` 项目的测试文件。

## 测试文件结构

- `linter.test.ts` - 单元测试，测试各个函数的独立功能
- `linter.integration.test.ts` - 集成测试，测试完整的代码解析和规则应用流程

## 运行测试

### 运行所有测试
```bash
npm test
```

### 运行测试并显示覆盖率
```bash
npm run test:coverage
```

### 运行测试（一次性）
```bash
npm run test:run
```

## 测试内容

### 单元测试 (`linter.test.ts`)

测试以下函数的独立功能：

1. **getCode** - 文件读取功能
   - 成功读取文件内容
   - 处理文件读取错误

2. **getAST** - AST 解析功能
   - 正确解析代码生成 AST

3. **getAllJsFile** - 文件扫描功能
   - 处理目录读取错误
   - 正确识别 JS 文件

4. **worker** - 单个文件处理功能
   - 处理单个文件
   - 处理文件读取失败的情况

5. **run** - 主运行函数
   - 处理指定路径的文件
   - 处理全局模式
   - 处理无参数情况

### 集成测试 (`linter.integration.test.ts`)

测试完整的代码解析和规则应用流程：

1. **实际代码解析测试**
   - 检测缺少分号的错误
   - 检测未使用的变量
   - 处理没有错误的代码

2. **配置文件测试**
   - 使用默认规则当配置文件不存在时
   - 正确处理配置文件格式错误

3. **全局模式测试**
   - 处理多个 JS 文件

## 测试技术栈

- **Vitest** - 测试框架
- **Mock** - 模拟依赖（fs, path, espree, estraverse, chalk）
- **TypeScript** - 类型安全的测试代码

## 注意事项

1. 测试使用了大量的 mock 来隔离外部依赖
2. 集成测试模拟了真实的代码解析场景
3. 测试覆盖了错误处理和边界情况
4. 所有测试都使用中文描述，便于理解测试目的 