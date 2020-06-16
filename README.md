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
 
1. prefs:root=General&path=About
2. prefs:root=General&path=ACCESSIBILITY
3. prefs:root=AIRPLANE_MODE
4. prefs:root=General&path=AUTOLOCK
5. prefs:root=General&path=USAGE/CELLULAR_USAGE
6. prefs:root=Brightness
7. prefs:root=Bluetooth
prefs:root=General&path=DATE_AND_TIME
prefs:root=FACETIME
prefs:root=General
prefs:root=General&path=Keyboard
prefs:root=CASTLE
prefs:root=CASTLE&path=STORAGE_AND_BACKUP
prefs:root=General&path=INTERNATIONAL
prefs:root=LOCATION_SERVICES
prefs:root=ACCOUNT_SETTINGS
prefs:root=MUSIC
prefs:root=MUSIC&path=EQ
prefs:root=MUSIC&path=VolumeLimit
prefs:root=General&path=Network
prefs:root=NIKE_PLUS_IPOD
prefs:root=NOTES
prefs:root=NOTIFICATIONS_ID
prefs:root=Phone
prefs:root=Photos
prefs:root=General&path=ManagedConfigurationList
prefs:root=General&path=Reset
prefs:root=Sounds&path=Ringtone
prefs:root=Safari
prefs:root=General&path=Assistant
prefs:root=Sounds
prefs:root=General&path=SOFTWARE_UPDATE_LINK
prefs:root=STORE
prefs:root=TWITTER
prefs:root=FACEBOOK
prefs:root=General&path=USAGE prefs:root=VIDEO
prefs:root=General&path=Network/VPN
prefs:root=Wallpaper
prefs:root=WIFI
prefs:root=INTERNET_TETHERING
prefs:root=Phone&path=Blocked
prefs:root=DO_NOT_DISTURB

On IOS 13
App-prefs:General&path=About
App-prefs:AIRPLANE_MODE
App-prefs:General&path=AUTOLOCK
App-prefs:Bluetooth
App-prefs:General&path=DATE_AND_TIME
App-prefs:FACETIME
App-prefs:General
App-prefs:General&path=Keyboard
App-prefs:CASTLE
App-prefs:CASTLE&path=STORAGE_AND_BACKUP
App-prefs:General&path=INTERNATIONAL
App-prefs:MUSIC
App-prefs:NOTES
App-prefs:NOTIFICATIONS_ID
App-prefs:Phone
App-prefs:Photos
App-prefs:General&path=ManagedConfigurationList
App-prefs:General&path=Reset
App-prefs:Sounds&path=Ringtone
App-prefs:Sounds
App-prefs:General&path=SOFTWARE_UPDATE_LINK
App-prefs:STORE
App-prefs:Wallpaper
App-prefs:WIFI
App-prefs:INTERNET_TETHERING
App-prefs:DO_NOT_DISTURB

Not tested

App-prefs:TWITTER (??)

App-prefs:FACEBOOK (??)
App-prefs:NIKE_PLUS_IPOD (??)
https://stackoverflow.com/questions/28152526/how-do-i-open-phone-settings-when-a-button-is-clicked

