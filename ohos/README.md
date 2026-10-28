# ColorPicker Compose 1.2.0 OHOS 独立入口

本入口直接编译同一 Fork 的 `colorpicker-compose/src/commonMain/kotlin` 中 21 份原源，不复制或改写生产源码。上游 [1.2.0](https://github.com/skydoves/colorpicker-compose/tree/85f81afbccaf5c0837e402686b8db9d67cc74c59) 的 sources JAR、POM、GMM、构建声明、Native 参考元数据和 Apache-2.0 LICENSE 原件与 SHA-256 随配方保留，来源清单保留 53 个公开 Native API 的索引。

临时根坐标为 `io.github.qsxs.cpf.colorpicker:colorpicker-compose:<version>`，版本为 `1.2.0-cpf11-preview-<sourceSHA12>-<runID>-<attempt>`。producer 使用 Kotlin/Native 2.4.20-0.1.0-08、Compose 1.12.0-0.1.0-11、Gradle 9.5.0、JDK 17 与内容锁定的共享工具 A（`d0cff88fd1ea2e4f08bb4409f1c802cca0c7f285`）。common metadata 保留原适配的标准 KGP 直接编译和受限 metadata 补充；OHOS x64/arm64 保留标准 KGP Native，原始的 runtime/foundation/ui `implementation`、root POM runtime 与 Native POM compile scope 均须验证。

手动 producer 工作流仅上传验收通过的隔离 staging，Pages 须单独受控发布；任何已存在的版本目录会拒绝写入。独立 consumer 在 Pages 发布后以主坐标解析 metadata、x64 和 arm64，并编译真实 ColorPicker 调用探针。其他平台继续使用上游对应变体。本配方尚未执行云端构建、发布或消费验收；link、runtime、设备和 Android/iOS 回归均未验证。
