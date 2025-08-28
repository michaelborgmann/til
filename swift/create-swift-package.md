# 📘 Today I Learned: How to Create a Swift Package (SPM)

Today I learned how to create a **Swift Package** from scratch, configure it, and publish it to a repository for reuse in projects.

---

## **1. Create the Package Locally**

```bash
mkdir MySwiftPackage
cd MySwiftPackage
swift package init --type library
```

This creates a standard Swift Package structure:

```
MySwiftPackage/
├─ Package.swift
├─ Sources/
│  └─ MySwiftPackage/
│     └─ MySwiftPackage.swift
└─ Tests/
   └─ MySwiftPackageTests/
```

---

## **2. Edit `Package.swift` (Optional)**

You can configure platform support, products, and targets.
For example, a simple iOS-only library:

```swift
// swift-tools-version: 6.1
// The swift-tools-version declares the minimum version of Swift required to build this package.

import PackageDescription

let package = Package(
    name: "MySwiftPackage",
    platforms: [
        .iOS(.v17) // Optional — limit platform support
    ],
    products: [
        .library(
            name: "MySwiftPackage",
            targets: ["MySwiftPackage"]
        ),
    ],
    targets: [
        .target(
            name: "MySwiftPackage"
        ),
        .testTarget(
            name: "MySwiftPackageTests",
            dependencies: ["MySwiftPackage"]
        ),
    ]
)
```

---

## **3. Add the Package to an App Workspace (Optional)**

If you're developing an app alongside your package:

* Go to **Xcode → Add Packages → Add Local…**
* Select your package folder.
* Benefit: You can edit and test the Swift Package directly within the app workspace.
* For **remote packages**, Xcode treats the source as read-only.

---

## **4. Commit & Push the Package**

Initialize a git repository if you haven’t already, then push:

```bash
git init
git add .
git commit -m "Initial commit: Create Swift Package"
git branch -M main
git remote add origin https://github.com/username/MySwiftPackage.git
git push -u origin main
```

---

## **5. Tag Your First Release**

Create a semantic version tag so SwiftPM can resolve it:

```bash
git tag v0.1.0
git push origin v0.1.0
```

After pushing the tag, your package is ready to be integrated remotely:

```swift
.package(url: "https://github.com/username/MySwiftPackage.git", from: "0.1.0")
```
