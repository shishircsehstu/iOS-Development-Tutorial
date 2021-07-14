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
### Button Select Sound Effict

        import AVFoundation
        
        let generator = UISelectionFeedbackGenerator()
        generator.selectionChanged()
       
### Play Video on Custom view

        private func addVideoPlayer(with asset: AVAsset, playerView: UIView) {
        
        let playerItem = AVPlayerItem(asset: asset)
        player = AVPlayer(playerItem: playerItem)
        /*
        NotificationCenter.default.addObserver(self, selector: #selector(TrimViewController.itemDidFinishPlaying(_:)),
                                               name: NSNotification.Name.AVPlayerItemDidPlayToEndTime, object: playerItem) */
        
        let layer: AVPlayerLayer = AVPlayerLayer(player: player)
        layer.backgroundColor = UIColor.black.cgColor
        layer.frame = CGRect(x: 0, y: 0, width: playerView.frame.width, height: playerView.frame.height)
        
        //print("baker test: layer frame: ", layer.frame)
        
        layer.videoGravity = .resizeAspect
        playerView.layer.sublayers?.forEach({$0.removeFromSuperlayer()})
        playerView.layer.addSublayer(layer)
        
        player?.play()
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

# Hide keyboard when tap to view
   
    func setupToHideKeyboardOnTapOnView()
      {
          let tap: UITapGestureRecognizer = UITapGestureRecognizer(
              target: self,
              action: #selector(dismissKeyboard))
          
          tap.cancelsTouchesInView = true
          view.addGestureRecognizer(tap)
      }
      
      @objc func dismissKeyboard()
      {
          view.endEditing(true)
      }
## PLace holder attribute

   
    func setPlaceHolderColor()
     {
        
        numTextField.attributedPlaceholder = NSAttributedString(string: "Enter number",
                                                                         attributes: [NSAttributedString.Key.foregroundColor: place_color])
             
                numTextField.font = UIFont(name: "Poppins-Regular", size: 13)!
        
        
        
     }
     
# Take screeshots


extension UIImage {
    
    class func takeScreenshot(view: UIView) -> UIImage? {
        
        // Create screenshot
        UIGraphicsBeginImageContext(view.bounds.size)
        
        view.layer.render(in: UIGraphicsGetCurrentContext()!)
        let screenshot:UIImage = UIGraphicsGetImageFromCurrentImageContext()!
        UIGraphicsEndImageContext()
        print("Taking Screenshot")
        
        UIGraphicsEndImageContext()
        return screenshot
    }
    
}

usage:

 UIGraphicsBeginImageContext(UIApplication.shared.keyWindow!.bounds.size)
        UIApplication.shared.keyWindow!.layer.render(in: UIGraphicsGetCurrentContext()!)
        let screenshot = UIGraphicsGetImageFromCurrentImageContext()
        UIGraphicsEndImageContext()


# Contact permission request

   
    func requestAccess() {
          switch CNContactStore.authorizationStatus(for: .contacts) {
              
          case .authorized:
              fatchContacts()
              break
          case .denied:
              self.givePermissionAlertForContact()
              break
              
          case .restricted, .notDetermined:
              
              let store = CNContactStore()
              store.requestAccess(for: .contacts) { granted, error in
                  if granted {
                      self.fatchContacts()
                  } else {
                      DispatchQueue.main.async {
                          self.givePermissionAlertForContact()
                      }
                  }
              }
          }
      }
      func givePermissionAlertForContact(){
          
          OperationQueue.main.addOperation() {
              
              
              let alert = UIAlertController(title: "Permission Required", message: "This app requires access to your contacts list to get your saved numbers. Please allow it on settings", preferredStyle: UIAlertController.Style.alert)
              
              alert.addAction(UIAlertAction(title: "Cancel", style: UIAlertAction.Style.default, handler: {(ACTION) in alert.dismiss(animated: true, completion: nil)
                  
                  print("No!!")
              }))
              
              alert.addAction(UIAlertAction(title: "Go to Settings", style: UIAlertAction.Style.default, handler: {(ACTION) in alert.dismiss(animated: true, completion: nil)
                  
                  
                  UIApplication.shared.open(URL(string: UIApplication.openSettingsURLString)!)
                  //  print("setting page")
                  
              }))
              
              self.present(alert,animated: true, completion: nil)
              // return
          }
      }
    
    
 # Set Button in Navigation Bar
 
    func setupNavBar() {
        
        
        
        // let searchController = UISearchController(searchResultsController: nil)
        // self.navigationItem.searchController = searchController
        
        rightButton.setImage(UIImage(named: "plusAdd"), for: .normal)
        
        //rightButton.setTitleColor(.purple, for: .normal)
        
        rightButton.addTarget(self, action: #selector(addBlockAction(_:)), for: .touchUpInside)
        rightButton.contentEdgeInsets = UIEdgeInsets(top: 0, left: 0, bottom: 10, right: 20)
        rightButton.tag = 1
        rightButton.frame = CGRect(x: self.view.frame.width, y: 0 , width: 50, height: 50)
        
        // rightButton.backgroundColor = .red
        
        navigationController?.navigationBar.addSubview(rightButton)
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
        
        navigationItem.title = "Spamlist"
        
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
## set intro as rootview

    func setIntroPageViewControllerAsRootViewController(){
        
        
        let window = UIWindow(frame: UIScreen.main.bounds)
        
        // let storyboard = UIStoryboard.init(name: "Intro", bundle: nil)
        let viewController =  IndroFirrstViewController.init(nibName: "IndroFirrstViewController", bundle: nil) // storyboard.instantiateViewController(withIdentifier: self.getIntroIdentifier()) as!
        let navigationController = UINavigationController.init(rootViewController: viewController)
        navigationController.navigationBar.isHidden = true
        
        window.rootViewController = navigationController
        self.window = window
        window.makeKeyAndVisible()
        
    }
    
## set tabbar as root view

    public func setTabViewControllerAsRootViewController(){
        
        let window = UIWindow(frame: UIScreen.main.bounds)
        
        let storyBoardName = IS_DEVICE_IPAD ? "Main_iPad" : "TabBar"
        
        let mainViewController = UIStoryboard(name: storyBoardName, bundle: nil).instantiateViewController(withIdentifier: "TabBarViewController") as!  UITabBarController
        
        
        window.rootViewController = mainViewController
        self.window = window
        window.makeKeyAndVisible()
        
    }
    
    
# Completion Handler

    
    func makeNme(originalName: String, completion: @escaping  (String?, Bool?) -> ()){
        
        let newName = originalName+"_okay"
        completion(newName,true)
    }
    //Usage
      makeNme(originalName: "Xyz") { (newName, flag)  in
            if let flag = flag{
                print(flag)
                print(newName!)
            }
        }
# Country Code and Calling Code

func initCountyCode()
    {
        
       //let locale = Locale.current
       // print(locale.regionCode!)
        
        CountryCode.append("AF")
        CountryCode.append("AL")
        CountryCode.append("DZ")
        CountryCode.append("AS")
        CountryCode.append("AD")
        
        CountryCode.append("AO")
        CountryCode.append("AI")
        CountryCode.append("AG")
        CountryCode.append("AR")
        CountryCode.append("AM")
        CountryCode.append("AW")
        CountryCode.append("AU")
        CountryCode.append("AT")
        CountryCode.append("AZ")
        CountryCode.append("BS")
        CountryCode.append("BH")
        CountryCode.append("BD")
        CountryCode.append("BB")
        
        CountryCode.append("BY")
        CountryCode.append("BE")
        CountryCode.append("BZ")
        CountryCode.append("BJ")
        
        CountryCode.append("BM")
        CountryCode.append("BT")
        CountryCode.append("BA")
        CountryCode.append("BW")
        
        
        CountryCode.append("BR")
        CountryCode.append("IO")
        CountryCode.append("BG")
        CountryCode.append("BF")
        
        
        
        CountryCode.append("BI")
        CountryCode.append("KH")
        CountryCode.append("CM")
        CountryCode.append("CA")
        
        
        CountryCode.append("CV")
        CountryCode.append("KY")
        CountryCode.append("CF")
        CountryCode.append("TD")
        
        
        CountryCode.append("CL")
        CountryCode.append("CN")
        CountryCode.append("CX")
        CountryCode.append("CO")
        
        CountryCode.append("KM")
        CountryCode.append("CG")
        CountryCode.append("CK")
        CountryCode.append("CR")
        
        
        CountryCode.append("HR")
        CountryCode.append("CU")
        CountryCode.append("CY")
        CountryCode.append("CZ")
        
        CountryCode.append("DK")
        CountryCode.append("DJ")
        CountryCode.append("DM")
        CountryCode.append("DO")
        
        CountryCode.append("EC")
        CountryCode.append("EG")
        CountryCode.append("SV")
        CountryCode.append("GQ")
        
        CountryCode.append("ER")
        CountryCode.append("EE")
        CountryCode.append("ET")
        CountryCode.append("FO")
        
        CountryCode.append("FJ")
        CountryCode.append("FI")
        CountryCode.append("FR")
        CountryCode.append("GF")
        
        
        CountryCode.append("PF")
        CountryCode.append("GA")
        CountryCode.append("GM")
        CountryCode.append("GE")
        
        CountryCode.append("DE")
        CountryCode.append("GH")
        CountryCode.append("GI")
        CountryCode.append("GR")
        
        CountryCode.append("GL")
        CountryCode.append("GD")
        CountryCode.append("GP")
        CountryCode.append("GU")
        
        CountryCode.append("GT")
        CountryCode.append("GN")
        CountryCode.append("GW")
        CountryCode.append("GY")
        
        
        CountryCode.append("HT")
        CountryCode.append("HN")
        CountryCode.append("HU")
        CountryCode.append("IS")
        
        CountryCode.append("IN")
        CountryCode.append("ID")
        CountryCode.append("IQ")
        CountryCode.append("IE")
        
        CountryCode.append("IL")
        CountryCode.append("IT")
        CountryCode.append("JM")
        CountryCode.append("JP")
        
        
        CountryCode.append("JO")
        CountryCode.append("KZ")
        CountryCode.append("KE")
        CountryCode.append("KI")
        
        
        
        CountryCode.append("KW")
        CountryCode.append("KG")
        CountryCode.append("LV")
        CountryCode.append("LB")
        
        CountryCode.append("LS")
        CountryCode.append("LR")
        CountryCode.append("LI")
        CountryCode.append("LT")
        
        CountryCode.append("LU")
        CountryCode.append("MG")
        CountryCode.append("MW")
        CountryCode.append("MY")
        
        CountryCode.append("MV")
        CountryCode.append("ML")
        CountryCode.append("MT")
        CountryCode.append("MH")
        
        CountryCode.append("MQ")
        CountryCode.append("MR")
        CountryCode.append("MU")
        CountryCode.append("YT")
        
        
        
        CountryCode.append("MX")
        CountryCode.append("MC")
        CountryCode.append("MN")
        CountryCode.append("ME")
        
        CountryCode.append("MS")
        CountryCode.append("MA")
        CountryCode.append("MM")
        CountryCode.append("NA")
        
        CountryCode.append("NR")
        CountryCode.append("NP")
        CountryCode.append("NL")
        CountryCode.append("AN")
        
        CountryCode.append("NC")
        CountryCode.append("NZ")
        CountryCode.append("NI")
        CountryCode.append("NE")
        
        
        CountryCode.append("NG")
        CountryCode.append("NU")
        CountryCode.append("NF")
        CountryCode.append("MP")
        
        CountryCode.append("NO")
        CountryCode.append("OM")
        CountryCode.append("PK")
        CountryCode.append("PW")
        
        
        CountryCode.append("PA")
        CountryCode.append("PG")
        CountryCode.append("PY")
        CountryCode.append("PE")
        
        
        CountryCode.append("PH")
        CountryCode.append("PL")
        CountryCode.append("PT")
        CountryCode.append("PR")
        
        CountryCode.append("QA")
        CountryCode.append("RO")
        CountryCode.append("RW")
        CountryCode.append("WS")
        
        CountryCode.append("SM")
        CountryCode.append("SA")
        CountryCode.append("SN")
        CountryCode.append("RS")
        
        CountryCode.append("SC")
        CountryCode.append("SL")
        CountryCode.append("SG")
        CountryCode.append("SK")
        
        CountryCode.append("SI")
        CountryCode.append("SB")
        CountryCode.append("ZA")
        CountryCode.append("GS")
        
        CountryCode.append("ES")
        CountryCode.append("LK")
        CountryCode.append("SD")
        CountryCode.append("SR")
        
        
        CountryCode.append("SZ")
        CountryCode.append("SE")
        CountryCode.append("CH")
        CountryCode.append("TJ")
        
        CountryCode.append("TH")
        CountryCode.append("TG")
        CountryCode.append("TK")
        CountryCode.append("TO")
        CountryCode.append("TT")
        CountryCode.append("TN")
        CountryCode.append("TR")
        CountryCode.append("TM")
        
        CountryCode.append("TC")
        CountryCode.append("TV")
        CountryCode.append("UG")
        CountryCode.append("UA")
        
        
        
        CountryCode.append("AE")
        CountryCode.append("GB")
        CountryCode.append("US")
        CountryCode.append("UY")
        
        CountryCode.append("UZ")
        CountryCode.append("VU")
        CountryCode.append("WF")
        CountryCode.append("YE")
        
        CountryCode.append("ZM")
        CountryCode.append("ZW")
        CountryCode.append("BO")
        CountryCode.append("BN")
        
        
        CountryCode.append("CC")
        CountryCode.append("CD")
        CountryCode.append("CI")
        CountryCode.append("FK")
        
        
        CountryCode.append("GG")
        CountryCode.append("VA")
        CountryCode.append("HK")
        CountryCode.append("IR")
        
        CountryCode.append("IM")
        CountryCode.append("JE")
        CountryCode.append("KP")
        CountryCode.append("KR")
        
        
        CountryCode.append("LA")
        CountryCode.append("LY")
        CountryCode.append("MO")
        CountryCode.append("MK")
        
        CountryCode.append("FM")
        CountryCode.append("MD")
        CountryCode.append("MZ")
        CountryCode.append("PS")
        
        CountryCode.append("PN")
        CountryCode.append("RE")
        CountryCode.append("RU")
        CountryCode.append("BL")
        
        CountryCode.append("SH")
        CountryCode.append("KN")
        CountryCode.append("LC")
        CountryCode.append("MF")
        
        CountryCode.append("PM")
        CountryCode.append("VC")
        CountryCode.append("ST")
        CountryCode.append("SO")
        
        CountryCode.append("SJ")
        CountryCode.append("SY")
        CountryCode.append("TW")
        CountryCode.append("TZ")
        
        CountryCode.append("TL")
        CountryCode.append("VE")
        CountryCode.append("VN")
        CountryCode.append("VG")
        
        CountryCode.append("VI")
        
        
        print(CountryCode.count)
        
        
        
        
        
    }
## Dictinary of colling code


var countryDictionary  = ["AF":"93",
                          "AL":"355",
                          "DZ":"213",
                          "AS":"1",
                          "AD":"376",
                          "AO":"244",
                          "AI":"1",
                          "AG":"1",
                          "AR":"54",
                          "AM":"374",
                          "AW":"297",
                          "AU":"61",
                          "AT":"43",
                          "AZ":"994",
                          "BS":"1",
                          "BH":"973",
                          "BD":"880",
                          "BB":"1",
                          "BY":"375",
                          "BE":"32",
                          "BZ":"501",
                          "BJ":"229",
                          "BM":"1",
                          "BT":"975",
                          "BA":"387",
                          "BW":"267",
                          "BR":"55",
                          "IO":"246",
                          "BG":"359",
                          "BF":"226",
                          "BI":"257",
                          "KH":"855",
                          "CM":"237",
                          "CA":"1",
                          "CV":"238",
                          "KY":"345",
                          "CF":"236",
                          "TD":"235",
                          "CL":"56",
                          "CN":"86",
                          "CX":"61",
                          "CO":"57",
                          "KM":"269",
                          "CG":"242",
                          "CK":"682",
                          "CR":"506",
                          "HR":"385",
                          "CU":"53",
                          "CY":"537",
                          "CZ":"420",
                          "DK":"45",
                          "DJ":"253",
                          "DM":"1",
                          "DO":"1",
                          "EC":"593",
                          "EG":"20",
                          "SV":"503",
                          "GQ":"240",
                          "ER":"291",
                          "EE":"372",
                          "ET":"251",
                          "FO":"298",
                          "FJ":"679",
                          "FI":"358",
                          "FR":"33",
                          "GF":"594",
                          "PF":"689",
                          "GA":"241",
                          "GM":"220",
                          "GE":"995",
                          "DE":"49",
                          "GH":"233",
                          "GI":"350",
                          "GR":"30",
                          "GL":"299",
                          "GD":"1",
                          "GP":"590",
                          "GU":"1",
                          "GT":"502",
                          "GN":"224",
                          "GW":"245",
                          "GY":"595",
                          "HT":"509",
                          "HN":"504",
                          "HU":"36",
                          "IS":"354",
                          "IN":"91",
                          "ID":"62",
                          "IQ":"964",
                          "IE":"353",
                          "IL":"972",
                          "IT":"39",
                          "JM":"1",
                          "JP":"81",
                          "JO":"962",
                          "KZ":"77",
                          "KE":"254",
                          "KI":"686",
                          "KW":"965",
                          "KG":"996",
                          "LV":"371",
                          "LB":"961",
                          "LS":"266",
                          "LR":"231",
                          "LI":"423",
                          "LT":"370",
                          "LU":"352",
                          "MG":"261",
                          "MW":"265",
                          "MY":"60",
                          "MV":"960",
                          "ML":"223",
                          "MT":"356",
                          "MH":"692",
                          "MQ":"596",
                          "MR":"222",
                          "MU":"230",
                          "YT":"262",
                          "MX":"52",
                          "MC":"377",
                          "MN":"976",
                          "ME":"382",
                          "MS":"1",
                          "MA":"212",
                          "MM":"95",
                          "NA":"264",
                          "NR":"674",
                          "NP":"977",
                          "NL":"31",
                          "AN":"599",
                          "NC":"687",
                          "NZ":"64",
                          "NI":"505",
                          "NE":"227",
                          "NG":"234",
                          "NU":"683",
                          "NF":"672",
                          "MP":"1",
                          "NO":"47",
                          "OM":"968",
                          "PK":"92",
                          "PW":"680",
                          "PA":"507",
                          "PG":"675",
                          "PY":"595",
                          "PE":"51",
                          "PH":"63",
                          "PL":"48",
                          "PT":"351",
                          "PR":"1",
                          "QA":"974",
                          "RO":"40",
                          "RW":"250",
                          "WS":"685",
                          "SM":"378",
                          "SA":"966",
                          "SN":"221",
                          "RS":"381",
                          "SC":"248",
                          "SL":"232",
                          "SG":"65",
                          "SK":"421",
                          "SI":"386",
                          "SB":"677",
                          "ZA":"27",
                          "GS":"500",
                          "ES":"34",
                          "LK":"94",
                          "SD":"249",
                          "SR":"597",
                          "SZ":"268",
                          "SE":"46",
                          "CH":"41",
                          "TJ":"992",
                          "TH":"66",
                          "TG":"228",
                          "TK":"690",
                          "TO":"676",
                          "TT":"1",
                          "TN":"216",
                          "TR":"90",
                          "TM":"993",
                          "TC":"1",
                          "TV":"688",
                          "UG":"256",
                          "UA":"380",
                          "AE":"971",
                          "GB":"44",
                          "US":"1",
                          "UY":"598",
                          "UZ":"998",
                          "VU":"678",
                          "WF":"681",
                          "YE":"967",
                          "ZM":"260",
                          "ZW":"263",
                          "BO":"591",
                          "BN":"673",
                          "CC":"61",
                          "CD":"243",
                          "CI":"225",
                          "FK":"500",
                          "GG":"44",
                          "VA":"379",
                          "HK":"852",
                          "IR":"98",
                          "IM":"44",
                          "JE":"44",
                          "KP":"850",
                          "KR":"82",
                          "LA":"856",
                          "LY":"218",
                          "MO":"853",
                          "MK":"389",
                          "FM":"691",
                          "MD":"373",
                          "MZ":"258",
                          "PS":"970",
                          "PN":"872",
                          "RE":"262",
                          "RU":"7",
                          "BL":"590",
                          "SH":"290",
                          "KN":"1",
                          "LC":"1",
                          "MF":"590",
                          "PM":"508",
                          "VC":"1",
                          "ST":"239",
                          "SO":"252",
                          "SJ":"47",
                          "SY":"963",
                          "TW":"886",
                          "TZ":"255",
                          "TL":"670",
                          "VE":"58",
                          "VN":"84",
                          "VG":"284",
                          "VI":"340"]

    
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



