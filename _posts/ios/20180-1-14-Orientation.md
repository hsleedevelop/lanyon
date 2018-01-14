---
layout: post
title: Change orientation a specific viewController
category: ios
tags: [ios, orientation]
---
 
1. In First, Set the orientation at AppDelegate
{% highlight swift %}
var enableAllOrientation = false
  func application(_ application: UIApplication, supportedInterfaceOrientationsFor window: UIWindow?) -> UIInterfaceOrientationMask {
      if (enableAllOrientation == true){
          return UIInterfaceOrientationMask.allButUpsideDown
      }
      return UIInterfaceOrientationMask.portrait
  }
{% endhighlight %}

2. Enable rotating orientation onto a specific viewController
{% highlight swift %}
override func viewWillAppear(_ animated: Bool) {
      super.viewWillAppear(animated)

    JDFacade.app.enableAllOrientation = true
}

override func viewWillDisappear(_ animated: Bool) {
    super.viewWillDisappear(animated)

    let value = UIInterfaceOrientation.portrait.rawValue
    UIDevice.current.setValue(value, forKey: "orientation")

    JDFacade.app.enableAllOrientation = false
}
{% endhighlight %}

<!-- ``` Swift -->
3. when back to the non-orientation viewController
{% highlight swift %}
  override func viewDidAppear(_ animated: Bool) {
      super.viewDidAppear(animated)

      let rect = CGRect(x: 0, y: 0, width: 375, height: 667)
      if let wrapperView = self.tabBarController?.view.subviews[0].subviews[0] {
          wrapperView.frame = rect
      }

      UIViewController.attemptRotationToDeviceOrientation()
  }
{% endhighlight %}
<!-- ``` -->