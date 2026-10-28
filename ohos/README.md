# ColorPicker Compose 1.2.0 OHOS 独立入口

本入口直接编译同一 Fork 的 `colorpicker-compose/src/commonMain/kotlin` 中 21 份原源，不复制或改写生产源码。上游 [1.2.0](https://github.com/skydoves/colorpicker-compose/tree/85f81afbccaf5c0837e402686b8db9d67cc74c59) 的 sources JAR、POM、GMM、构建声明、Native 参考元数据和 Apache-2.0 LICENSE 原件与 SHA-256 随配方保留，来源清单保留 53 个公开 Native API 的索引。

临时根坐标为 `io.github.qsxs.cpf.colorpicker:colorpicker-compose:<version>`，版本为 `1.2.0-cpf11-preview-<sourceSHA12>-<runID>-<attempt>`。producer 使用 Kotlin/Native 2.4.20-0.1.0-08、Compose 1.12.0-0.1.0-11、Gradle 9.5.0、JDK 17 与内容锁定的共享工具 A（`d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`）。common metadata 保留原适配的标准 KGP 直接编译和受限 metadata 补充；OHOS x64/arm64 保留标准 KGP Native，原始的 runtime/foundation/ui `implementation`、root POM runtime 与 Native POM compile scope 均须验证。

## 已验版本与公开消费

[Fork source `779519a9bc21278c9496a11c43828dc194cbe64c`](https://github.com/qsxs/colorpicker-compose/commit/779519a9bc21278c9496a11c43828dc194cbe64c) 经 [producer 40674004251/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40674004251/attempts/1) 完成完整 21 份原源的生产与 staging 验证。已验根 GAV：`io.github.qsxs.cpf.colorpicker:colorpicker-compose:1.2.0-cpf11-preview-779519a9bc21-40674004251-1`。临时 Maven 根 `https://qsxs.github.io/cpf-maven/`（[实际根 POM](https://qsxs.github.io/cpf-maven/io/github/qsxs/cpf/colorpicker/colorpicker-compose/1.2.0-cpf11-preview-779519a9bc21-40674004251-1/colorpicker-compose-1.2.0-cpf11-preview-779519a9bc21-40674004251-1.pom)、[GitHub 制品仓库](https://github.com/qsxs/cpf-maven)）。

两次已验工作流的实际提交 B 均为 `abadbfb0b5c33b35dfafdb966e8e759276c5de45`，与共享工具内容锁 A 分别记录。工作流成功时上传通过 Verify 的 staging，并另上传证据；Pages 由维护者核对后手动发布。[Pages 制品提交 `af5af74fb640`](https://github.com/qsxs/cpf-maven/commit/af5af74fb6409cb9d2bc165253594e583ac8c4c2) 的 140 个文件、606,736 字节与 staging 经匿名 HTTP 逐字节对齐。

Producer 的 OHOS x64 和 arm64 各核验 53 个不同 API 名称；检查包括 50 个 Native metadata 签名名称与另外 8 个枚举生成成员的 Native IR 签名，不能将两组数量直接相加。三个目标均验证实际使用的原有 Compose 与 serialization 两个 `2.4.20-0.1.0-08` 编译器插件；库的 Compose runtime/foundation/ui 依赖仍为 `implementation`。

[consumer 40676245219/1](https://github.com/qsxs/cpf-port-tooling/actions/runs/40676245219/attempts/1) 使用 Gradle 9.5.0，从公开根 GAV 经 GMM 完成 common metadata、OHOS x64 和 arm64 真实编译。唯一探针覆盖 `HsvColorPicker` 的 `initialColor`/`onColorChanged`、`BrightnessSlider`、`ColorEnvelope.color` 和 `selectByColor(color, true)`；12 个公开对象与 staging 对齐，均首次请求成功。

只验证 Gradle 9.5.0 消费，未单独验证 Gradle 8.11.1；link、runtime、设备和 Android/iOS 回归均未运行。App 引用尚未切换，其他平台继续使用上游对应变体。
