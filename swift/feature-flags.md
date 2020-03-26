# Feature-Flags
post-date: 26.03.20

John Sundell does a really great job demonstrating the use of feature-flags as a possible solution for managing the addition
of features for different users ("A/B testing") and their different devices (OS Version, hardware capability and
what have you). See the article: [Feature flags in Swift | Swift by Sundell](https://www.swiftbysundell.com/articles/feature-flags-in-swift/)

I came across his great case for Feature-Flags, when reading another article from him about handling new Swift technologies
and the following snippet, where the elegant use of Feature-Flags is demonstrated (s. line #12 in following snippet):
``` swift
func presentPromotion(in presentingViewController: UIViewController) {
    // Using this statement will let us assume that the rest
    // of this function will only be executed on iOS 13 and above:
    guard #available(iOS 13, *) else {
        return
    }
    
    // We also add a dynamic feature flag that'll let us control
    // whether our promotion feature will be enabled at runtime,
    // essentially acting as an additional safety mechanism in
    // case something goes wrong and we need to disable it:
    guard featureFlags.enablePromotion else {
        return
    }

    // We can now use iOS 13-only APIs without any problems:
    let view = PromotionView()
    let viewController = UIHostingController(rootView: view)
    presentingViewController.present(viewController, animated: true)
}
```
