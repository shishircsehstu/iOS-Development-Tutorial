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
5. MSPeekCollectionViewDelegateImplementation: https://github.com/MaherKSantina/MSPeekCollectionViewDelegateImplementation

# Animation:

        UIView.animate(withDuration: 0.4, animations: {
            self.datePickerView.frame.origin.y = DEVICE_HEIGHT
            self.datePickerViewColore.backgroundColor = .clear
            
        }) { (finish) in
            self.datePickerViewColore.frame.origin.y = DEVICE_HEIGHT
        }
## Loop Animation
 
    func startAnimation()
    {
        UIView.animate(withDuration: 2.0, delay: 0, options: [.repeat, .autoreverse], animations: {

           // self.animationView.frame = CGRect(x: 150, y: 220, width: 100, height: 100)
            self.animationView.backgroundColor = .red
            self.animationView.layer.cornerRadius = self.animationView.frame.size.height/2

        }, completion: { (finished: Bool) -> Void in
            print("test")
        })
    }

    @IBAction func startAction(_ sender: Any) {
        startAnimation()
    }
    @IBAction func stopAction(_ sender: Any) {
        animationView.layer.removeAllAnimations()
    }


# Notification

      NotificationCenter.default.post(name: Notification.Name("RELOAD_COLLECTION_VIEW"), object: nil, userInfo: nil)
      
       NotificationCenter.default.addObserver(self, selector: #selector(reloadCollectonView), name: NSNotification.Name(rawValue: "RELOAD_COLLECTION_VIEW"), object: nil)
          @objc func reloadCollectonView(){
          }
          
          
  ## SetTitleTextAttribute
  
             UIBarButtonItem.appearance().setTitleTextAttributes([NSAttributedString.Key.font: UIFont(name: "Poppins-Regular", size: 18)!], for: .normal)
        navigationItem.backBarButtonItem = UIBarButtonItem(title: "Back", style: .plain, target: nil, action: nil)
        self.navigationController?.navigationBar.topItem?.backBarButtonItem?.setTitleTextAttributes([NSAttributedString.Key.font: UIFont(name: "Poppins-Regular", size: 18)!], for: .normal)
        
# Get Selected cell from button on Collection view cell

### UICollectionViewCell

protocol cellDelegate {



    func sendInfo()
    func deselectDetection(cellButton: UIButton
 }

class DuplicateCollectionViewCell: UICollectionViewCell {
    
    @IBOutlet weak var tickButton: UIButton!{  //clecked button
        didSet{
            
            self.tickButton.addTarget(self, action: #selector(ticButtonAction(_:)), for: .touchDragInside)
        }
    }
    @IBOutlet weak var dupImages: UIImageView!
    
    
    var tickOrnot = 0
    var delegate: cellDelegate!
    
    var arrayIn = Int()
    var valueIn = Int()
    var deleteAsset = PHAsset()
    
    override func awakeFromNib() {
        super.awakeFromNib()
        
        dupImages.layer.cornerRadius = 9
        
        
    }
    
    override func prepareForReuse() {
        super.prepareForReuse()
        
        self.dupImages.image = nil
    }
    
    
    @objc private func ticButtonAction(_ sender: UIButton) {
        
        
        if self.delegate != nil{
            self.delegate.deselectDetection(cellButton: sender)
        }
        
    }}

### Your VC





   func deselectDetection(cellButton: UIButton) {
   
   
   
        guard let cell = cellButton.superview?.superview as? DuplicateCollectionViewCell else {
            return // or fatalError() or whatever
        }
        
        
        if let indexPath = myCollectionView.indexPath(for: cell){
            if index == 0{
                if deselectedIndexPathArray.contains(indexPath){
                    if let index = deselectedIndexPathArray.firstIndex(of: indexPath){
                        
                        cell.tickButton.setImage(UIImage(named: "tick_dis"), for: .normal)
                        cell.backgroundColor = .white
                        deselectedIndexPathArray.remove(at: index)
                    }
                }
                else{
                    cell.tickButton.setImage(UIImage(named: "tick"), for: .normal)
                    cell.backgroundColor = UIColor(displayP3Red: 24/255, green: 176/255, blue: 245/255, alpha: 1)
                    deselectedIndexPathArray.append(indexPath)
                }
            }}


# Json parsing 

struct details: Decodable {
    var name: String
    var description: String
    var courses: [allItems]
}
struct  allItems: Decodable {
    var id : Int
    var imageUrl: String
    var link: String
    var name: String
    
}

class ViewController: UIViewController {
    
    @IBOutlet weak var imageViewOut: UIImageView!
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        
        let urlStr = "https://api.letsbuildthatapp.com/jsondecodable/website_description"
        
        let session = URLSession.shared
        
        
        guard let url = URL(string: urlStr) else {
            return
        }
        session.dataTask(with: url) { (data, response, err) in
            
            guard let data = data else{return}
            
            print(data.base64EncodedData())
            do{
                //                let jsonn  = try JSONSerialization.jsonObject(with: data, options: .mutableContainers) as? [String: Any]
                //
                //                guard let newJson = jsonn else{return}
                //                let items = allItems(json: newJson )
                
                let json  =  try JSONDecoder().decode(details.self, from: data)
                
                print(json.name)
                print(json.description)
                print(json.courses.count)
                
                for newJson in json.courses
                {
                    print(newJson.id)
                    print(newJson.imageUrl)
                    print(newJson.link)
                    print(newJson.name)
                    
                    print("=================================\n")
                    
                    
                    
                    let url = URL(string: newJson.imageUrl)
                    let data = try? Data(contentsOf: url!)
                    DispatchQueue.main.async() {
                        self.imageViewOut.image = UIImage(data: data!)
                    }
                    
                }
                
                //                print(json.id)
                //                print(json.imageUrl)
                //                print(json.link)
                //                print(json.name)
            }
            catch let jeerr
            {
                print(jeerr.localizedDescription)
            }
        }.resume()
    }
}

# Set right bar button and set large nav bar 

func setupNavBar() {
        
        // let searchController = UISearchController(searchResultsController: nil)
        // self.navigationItem.searchController = searchController
        
        let rightButton = UIButton()
        rightButton.setImage(UIImage(named: "plusAdd"), for: .normal)
        
        //rightButton.setTitleColor(.purple, for: .normal)
        
        rightButton.addTarget(self, action: #selector(addBlockAction(_:)), for: .touchUpInside)
        navigationController?.navigationBar.addSubview(rightButton)
        rightButton.tag = 1
        rightButton.frame = CGRect(x: self.view.frame.width, y: 0 , width: 50, height: 50)
        
        let targetView = self.navigationController?.navigationBar
        
        let trailingContraint = NSLayoutConstraint(item: rightButton, attribute:
            .trailingMargin, relatedBy: .equal, toItem: targetView,
                             attribute: .trailingMargin, multiplier: 1.0, constant: -16)
        let bottomConstraint = NSLayoutConstraint(item: rightButton, attribute: .bottom, relatedBy: .equal,
                                                  toItem: targetView, attribute: .bottom, multiplier: 1.0, constant: -6)
        
        rightButton.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([trailingContraint, bottomConstraint])
        
        
        
        self.navigationController?.navigationBar.isTranslucent = true
        
        self.navigationController?.navigationBar.barTintColor = VIEW_BG_COLOR
        
        navigationItem.title = "Blacklist"
        
        let textAttributes = [NSAttributedString.Key.foregroundColor:UIColor.white]
        navigationController?.navigationBar.titleTextAttributes = textAttributes
        
        
        navigationController?.navigationBar.largeTitleTextAttributes =
            [NSAttributedString.Key.foregroundColor: UIColor(displayP3Red: 255/255, green: 255/255, blue: 255/255, alpha: 1),
             
             NSAttributedString.Key.font: UIFont(name: "Poppins-Medium", size: 30) ??
                UIFont.systemFont(ofSize: 30)]
        
        
        if #available(iOS 11.0, *) {
            navigationController?.navigationBar.prefersLargeTitles = true
            navigationController?.navigationItem.largeTitleDisplayMode = .automatic
        }
        
        
        
    }

# Data Source and Delegat
- In the MVC  datasource is in the model layer and the delegate is in the control layer.
The datasource supplies the data, the delegate supplies the behavior.
- Delegate relates to the UI and User actions against the cells and table
common methods: willSelectRow, didSelectRow, willDisplay, heightForRow, willBeginEditingAt
- Data Source deals with the editing, population and displaying of data on the tableview.
common methods canEditRowAt, commit, titleForHeaderInSection, cellForRowAt, numberOfSections, sectionIndexTitles
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



