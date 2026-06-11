# Log

A lightweight logging utility that supports multiple output methods.

Each log message includes debugging information such as:
 - Timestamp
 - Log level
 - Category
 - Thread identifier
 - Source file and line number
 - Function name

## Example output
```text
2026-06-11T06:21:15.782Z [DEBUG] [LifeCycle] [MainThread] [SplashViewController.swift:21] [init(viewModel:)]
SplashViewController init
```

## Recommended Usage

```swift
public struct Log {
    
    private enum LoggerType: String {
        case main = "Main"
        case network = "Network"
        case lifeCycle = "LifeCycle"
    }
    
    private static let main = ConsoleLogger(category: LoggerType.main.rawValue)
    
    public static let network = ConsoleLogger(category: LoggerType.network.rawValue)
    public static let lifeCycle = ConsoleLogger(category: LoggerType.lifeCycle.rawValue)
    
    private init() {}
    
    public static func d(_ objects: Any?..., separator: String = " ", method: ConsoleLogger.OutputMethod = .oslog, filename: String = #fileID, line: Int = #line, funcName: StaticString = #function) {
        main.d(objects, separator: separator, method: method, filename: filename, line: line, funcName: funcName)
    }
    
    public static func i(_ objects: Any?..., separator: String = " ", method: ConsoleLogger.OutputMethod = .oslog, filename: String = #fileID, line: Int = #line, funcName: StaticString = #function) {
        main.i(objects, separator: separator, method: method, filename: filename, line: line, funcName: funcName)
    }
    
    public static func n(_ objects: Any?..., separator: String = " ", method: ConsoleLogger.OutputMethod = .oslog, filename: String = #fileID, line: Int = #line, funcName: StaticString = #function) {
        main.n(objects, separator: separator, method: method, filename: filename, line: line, funcName: funcName)
    }
    
    public static func e(_ objects: Any?..., separator: String = " ", method: ConsoleLogger.OutputMethod = .oslog, filename: String = #fileID, line: Int = #line, funcName: StaticString = #function) {
        main.e(objects, separator: separator, method: method, filename: filename, line: line, funcName: funcName)
    }
    
    public static func f(_ objects: Any?..., separator: String = " ", method: ConsoleLogger.OutputMethod = .oslog, filename: String = #fileID, line: Int = #line, funcName: StaticString = #function) {
        main.f(objects, separator: separator, method: method, filename: filename, line: line, funcName: funcName)
    }
}
```
