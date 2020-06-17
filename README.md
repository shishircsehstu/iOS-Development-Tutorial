# Swift Programmig Language
1. Swift Programming Language: https://www.tutorialspoint.com/swift/index.htm
2. Swift Programming Language: https://docs.swift.org/swift-book/GuidedTour/GuidedTour.html

# iOS (Swift) Development Tutorials:
1. Document Directory: https://vasundharavision.com/blog/ios/save-and-get-image-from-document-directory
2. Document Directory:  https://stackoverflow.com/questions/54290842/how-to-store-files-in-folder-which-is-created-by-using-documentdirectory-swift
3. Core Data: https://medium.com/@ankurvekariya/core-data-crud-with-swift-4-2-for-beginners-40efe4e7d1cc
4. Alamofire: https://codewithchris.com/alamofire/
5. Alamofire: https://www.raywenderlich.com/6587213-alamofire-5-tutorial-for-ios-getting-started
6. Alamofire: https://www.codementor.io/@ashishkakkad/how-to-use-alamofire-and-swiftyjson-with-swift-4or6su5oa
7. NotificationCenter: https://stackoverflow.com/questions/30328452/how-to-pass-multiple-values-with-a-notification-in-swift
# Custom Collection view
1. Custom Collection view: https://itnext.io/programmatic-custom-collectionview-cell-subclass-in-swift-5-xcode-10-291f8d41fdb1
2. Custom layout: https://github.com/rubygarage/collection-view-layouts
3. Custom Coleection View: https://github.com/abdullahselek/ASCollectionView
4. CollectionView Batch Update: https://gist.github.com/phongsakornp/4870b46a9ba4208e5ff0

# Animation:

        UIView.animate(withDuration: 0.4, animations: {
            self.datePickerView.frame.origin.y = DEVICE_HEIGHT
            self.datePickerViewColore.backgroundColor = .clear
            
        }) { (finish) in
            self.datePickerViewColore.frame.origin.y = DEVICE_HEIGHT
        }
# Settings options

UIApplication.shared.open(URL(string: "App-prefs:Phone")!)
## On IOS 13
1. App-prefs:General&path=About
2. App-prefs:AIRPLANE_MODE
3. App-prefs:General&path=AUTOLOCK
4. App-prefs:Bluetooth
5. App-prefs:General&path=DATE_AND_TIME
6. App-prefs:FACETIME
7. App-prefs:General
8. App-prefs:General&path=Keyboard
9. App-prefs:CASTLE
10. App-prefs:CASTLE&path=STORAGE_AND_BACKUP
11. App-prefs:General&path=INTERNATIONAL
12. App-prefs:MUSIC
13. App-prefs:NOTES
14. App-prefs:NOTIFICATIONS_ID
15. App-prefs:Phone
16. App-prefs:Photos
17. App-prefs:General&path=ManagedConfigurationList
18. App-prefs:General&path=Reset
19. App-prefs:Sounds&path=Ringtone
20. App-prefs:Sounds
21. App-prefs:General&path=SOFTWARE_UPDATE_LINK
22. App-prefs:STORE
23. App-prefs:Wallpaper
24. App-prefs:WIFI
25. App-prefs:INTERNET_TETHERING
26. App-prefs:DO_NOT_DISTURB

## iOS<13
1. prefs:root=General&path=About
2. prefs:root=General&path=ACCESSIBILITY
3. prefs:root=AIRPLANE_MODE
4. prefs:root=General&path=AUTOLOCK
5. prefs:root=General&path=USAGE/CELLULAR_USAGE
6. prefs:root=Brightness
7. prefs:root=Bluetooth
8. prefs:root=General&path=DATE_AND_TIME
9. prefs:root=FACETIME
10. prefs:root=General
11. prefs:root=General&path=Keyboard
12. prefs:root=CASTLE
13. prefs:root=CASTLE&path=STORAGE_AND_BACKUP
14. prefs:root=General&path=INTERNATIONAL
15. prefs:root=LOCATION_SERVICES
16. prefs:root=ACCOUNT_SETTINGS
17. prefs:root=MUSIC
18. prefs:root=MUSIC&path=EQ
19. prefs:root=MUSIC&path=VolumeLimit
20. prefs:root=General&path=Network
21. prefs:root=NIKE_PLUS_IPOD
22. prefs:root=NOTES
23. prefs:root=NOTIFICATIONS_ID
24. prefs:root=Phone
25. prefs:root=Photos
26. prefs:root=General&path=ManagedConfigurationList
27. prefs:root=General&path=Reset
28. prefs:root=Sounds&path=Ringtone
29. prefs:root=Safari
30. prefs:root=General&path=Assistant
31. prefs:root=Sounds
32. prefs:root=General&path=SOFTWARE_UPDATE_LINK
33. prefs:root=STORE
34. prefs:root=TWITTER
35. prefs:root=FACEBOOK
36. prefs:root=General&path=USAGE prefs:root=VIDEO
37. prefs:root=General&path=Network/VPN
38. prefs:root=Wallpaper
39. prefs:root=WIFI
40. prefs:root=INTERNET_TETHERING
41. prefs:root=Phone&path=Blocked
42. prefs:root=DO_NOT_DISTURB


Not tested

App-prefs:TWITTER (??)

App-prefs:FACEBOOK (??)
App-prefs:NIKE_PLUS_IPOD (??)
https://stackoverflow.com/questions/28152526/how-do-i-open-phone-settings-when-a-button-is-clicked

#Loop Animation:
func startAnimation()
    {
        UIView.animate(withDuration: 2.0, delay: 0, options: [.repeat, .autoreverse], animations: {

           // self.animationView.frame = CGRect(x: 150, y: 220, width: animationView.l, height: 100)
            self.animationView.backgroundColor = .red
            self.animationView.layer.cornerRadius = self.animationView.frame.size.height/2

        }, completion: { (finished: Bool) -> Void in
            print("test")

            
        })
    }

    @IBAction func startAction(_ sender: Any) {
        startAnimation()
        //
        
    }
    @IBAction func stopAction(_ sender: Any) {
        animationView.layer.removeAllAnimations()
        
    }

