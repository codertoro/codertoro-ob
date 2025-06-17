---
{"type":"java","title":"13-Java 的 类加载机制","tags":["projects/es6"],"author":"codertoro","establish":"2025-05-27","update":"2025/05/27 17:44","dg-publish":true,"permalink":"/Projects/07-Java/13-Java 的 类加载机制/","dgPassFrontmatter":true,"created":"2025-05-27T17:44:37.004+08:00","updated":"2025-05-27T17:44:55.621+08:00"}
---

**`DBUtil.class.getClassLoader().getResourceAsStream("config.properties")` 能够找到配置文件，是因为 Java 的 类加载机制（ClassLoader） 会从 类路径（Classpath） 中查找资源文件。它的工作原理如下：**

---

### 0.1.1. **1. `ClassLoader` 的作用**

`ClassLoader` 是 Java 加载 `.class` 文件和资源文件（如 `.properties`、`.xml` 等）的核心机制。它负责：

- 加载 `.class` 文件到 JVM 中
- 查找并读取类路径（Classpath）下的资源文件（如 `config.properties`）

---

### 0.1.2. **2. `getResourceAsStream()` 如何查找文件？**

`getResourceAsStream(String name)` 方法会在 **类路径（Classpath）** 中查找指定名称的资源文件，并返回一个 `InputStream`。它的查找逻辑如下：

#### **(1) 查找范围**

- **类路径（Classpath）** 包括：
    - `src/main/resources/`（Maven/Gradle 项目的标准资源目录）
    - `src/`（传统 Java 项目的资源目录）
    - `target/classes/`（Maven 编译后 `.class` 和资源文件的输出目录）
    - JAR 包中的文件（如果资源被打包进 JAR）
    - 其他手动添加到 Classpath 的目录

#### **(2) 查找方式**

- **`getResourceAsStream("config.properties")`**  
    表示从 **类路径的根目录** 查找 `config.properties` 文件。
    
    - 如果文件在 `src/main/resources/config.properties`，则可以直接找到。
    - 如果文件在 `src/main/resources/com/example/config.properties`，则需要写完整路径：  
        `getResourceAsStream("com/example/config.properties")`
- **`getResourceAsStream("/config.properties")`**  
    如果加了 `/`，仍然表示从类路径的根目录查找（和上面一样）。
    

---

### 0.1.3. **3. 为什么 `FileReader` 不能用相对路径，而 `getResourceAsStream` 可以？**

|方式|查找依据|适用场景|问题|
|---|---|---|---|
|`FileReader("config.properties")`|基于 **当前工作目录（Working Directory）**|本地文件系统|工作目录可能因运行方式（IDE、命令行、JAR）不同而变化，导致找不到文件|
|`getResourceAsStream("config.properties")`|基于 **类路径（Classpath）**|JAR 包、IDE、服务器环境|稳定，只要文件在 Classpath 中就能找到|

#### **`FileReader` 的问题**

- 如果使用 `new FileReader("config.properties")`，Java 会在 **当前工作目录**（通常是项目根目录或模块目录）查找文件。
- 如果通过 `java -jar` 运行 JAR 包，工作目录可能不同，导致找不到文件。
- 如果文件在 `src/main/resources/` 里，编译后会被复制到 `target/classes/`，`FileReader` 仍然找不到。

#### **`getResourceAsStream` 的优势**

- 无论文件是在 `src/main/resources/` 还是打包进 JAR，只要它在 Classpath 中，就能被找到。
- 适用于各种运行环境（IDE、命令行、Tomcat 服务器等）。

---

### 0.1.4. **4. 如何确保 `config.properties` 能被正确加载？**

#### **(1) 文件位置**

- **Maven/Gradle 项目**：放在 `src/main/resources/config.properties`  
    （编译后会自动复制到 `target/classes/config.properties`）
- **传统 Java 项目**：放在 `src/` 或手动添加到 Classpath

#### **(2) 代码加载方式**

```java
// 推荐方式：使用 ClassLoader
try (InputStream in = DBUtil.class.getClassLoader().getResourceAsStream("config.properties")) {
    if (in == null) {
        throw new RuntimeException("配置文件 config.properties 未找到！");
    }
    Properties props = new Properties();
    props.load(in);
    // 读取配置...
} catch (IOException e) {
    throw new RuntimeException("加载配置文件失败", e);
}
```

---

### 0.1.5. **5. 总结**

|关键点|说明|
|---|---|
|**`ClassLoader`**|负责从 Classpath 加载 `.class` 和资源文件|
|**`getResourceAsStream()`**|从 Classpath 根目录查找文件，返回 `InputStream`|
|**`src/main/resources/`**|Maven/Gradle 项目的标准资源目录|
|**`FileReader` 的问题**|依赖工作目录，不可靠|
|**`getResourceAsStream` 的优势**|适用于 JAR、IDE、服务器环境，稳定可靠|

这样，无论你的项目是在 IDE 中运行，还是打包成 JAR 文件，`getResourceAsStream` 都能正确找到 `config.properties`！ 🚀