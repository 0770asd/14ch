# 비디오 재생 앱
## ViewConrtoller

### 비디오 파일명을 사용하여 비디오가 저장된 앱 내붕의 파일를 받아옴

```javascript
import UIKit
import AVKit
 
class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }
    @IBAction func btnPlayInternalMovie(_ sender: UIButton) {
        // 내부 파일  mp4
        let filePath:String? = Bundle.main.path(forResource: "FastTyping", ofType: "mp4")
        let url = NSURL(fileURLWithPath: filePath!)
        playVideo(url: url)
    }
```


### 외부에 링크된 주소를 NSURL 형식으로 변경

```javascript

    @IBAction func btnPlayExternalMovie(_ sender: UIButton) {
        // 외부 파일 mp4
        let url = NSURL(string: "https://dl.dropboxusercontent.com/s/e38auz050w2mcud/Fireworks.mp4")!
        
        playVideo(url: url)
    }
```


### AVPlayerViewController의 인스턴스를 생성

```javascript
private func playVideo(url: NSURL) {
        let playerController = AVPlayerViewController()

        let player = AVPlayer(url: url as URL)
        playerController.player = player

        self.present(playerController, animated: true) {
            player.play()
        }
    }
}
```


## AppDelegate

```javascript
import UIKit

@main

class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.

        return true

    }
    // MARK: UISceneSession Lifecycle

    func application(_ application: UIApplication, configurationForConnecting connectingSceneSession: UISceneSession, options: UIScene.ConnectionOptions) -> UISceneConfiguration {
        // Called when a new scene session is being created.
        // Use this method to select a configuration to create the new scene with.

        return UISceneConfiguration(name: "Default Configuration", sessionRole: connectingSceneSession.role)
    }
    func application(_ application: UIApplication, didDiscardSceneSessions sceneSessions: Set<UISceneSession>) {
        // Called when the user discards a scene session.
        // If any sessions were discarded while the application was not running, this will be called shortly after application:didFinishLaunchingWithOptions.
        // Use this method to release any resources that were specific to the discarded scenes, as they will not return.
    }
}
```


## 동작

<img src="https://user-images.githubusercontent.com/106363908/174169082-ee1e1ce7-0031-42ff-b0f0-8585fed0e7a2.png" width="400" height="600">

<img src="https://user-images.githubusercontent.com/106363908/174169114-ef10f1f3-cf78-47f6-bea4-a931af5538b3.png" width="400" height="600">

