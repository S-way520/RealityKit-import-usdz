# RealityKit-import-usdz
SwiftUI + RealityKit import usdz/reality
# The first part
![IMG_0141](https://github.com/S-way520/RealityKit-import-usdz/assets/95877651/db519e68-c0bb-4317-8e9d-264004c59298)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import RealityKit
struct ContentView: View {
    var body: some View {
        ARViewContainer().edgesIgnoringSafeArea(.all)
    }
}
struct ARViewContainer: UIViewRepresentable {
    func makeUIView(context: Context) -> ARView {
        let arView = ARView(frame: .zero, cameraMode: .ar, automaticallyConfigureSession: true)
        let anchorEntity = AnchorEntity(plane: .horizontal)
        guard let ARentity = try? ModelEntity.load(named: "tutorial") else {
            fatalError("tutorial model is not!")//usdz/reality
        }
        anchorEntity.addChild(ARentity)
        arView.scene.anchors.append(anchorEntity)
        return arView
    }
    func updateUIView(_ uiView: ARView, context: Context) {
    }
}
```
