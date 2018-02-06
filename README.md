
=======================>left bar
class LeftDrawerVC: UIViewController,UITableViewDelegate,UITableViewDataSource,UIGestureRecognizerDelegate {

    @IBOutlet weak var tblMenu: UITableView!
    let arrayTitles = ["","MY CUSTOMER","MY ACTIVITIES","CHANGE PASSWORD","ABOUT US","NOTIFICATION","LOGOUT"]
    let ArrayImage = ["","menu_my_customer","menu_my_activites","menu_edit_profile","menu_about_us","menu_notification","menu_logout"]
    override func viewDidLoad() {
        super.viewDidLoad()
  
    }
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        self.tblMenu.reloadData()
    }
    var mainVC = UIViewController()
    
    //MARK:-tableView Controller method
    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        if (indexPath as NSIndexPath).row == 0 {
            return 190
        }
        else if indexPath.row == arrayTitles.count{
            return 45
        }
        return 45
    }
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return arrayTitles.count
    }
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        if indexPath.row == 0 {
            let cellHeaders : MenuCell = tableView.dequeueReusableCell(withIdentifier: "HeaderCell") as! MenuCell
            
            
            let tapGestureRecognizer = UITapGestureRecognizer(target: self, action: #selector(imageTapped(tapGestureRecognizer:)))
            cellHeaders.ImgProfile.isUserInteractionEnabled = true
            cellHeaders.ImgProfile.addGestureRecognizer(tapGestureRecognizer)
            let FullName = Pref.getObjectForKey(KprofileName)
            cellHeaders.lblProfileName.text = FullName as? String
            cellHeaders.ImgProfile.layer.cornerRadius = cellHeaders.ImgProfile.bounds.size.height/2
            cellHeaders.ImgProfile.layer.borderWidth = 1.5
            cellHeaders.ImgProfile.layer.borderColor = UIColor.white.cgColor
            cellHeaders.ImgProfile.clipsToBounds = true
            
           
        
            return cellHeaders
        }
        else {
            let cell: MenuCell = tableView.dequeueReusableCell(withIdentifier: "Cell") as! MenuCell
            cell.imgMenu.image = UIImage(named:ArrayImage[indexPath.row])
            cell.lblmenuName.text = arrayTitles[indexPath.row]
            return cell
        }
    }
    func imageTapped(tapGestureRecognizer: UITapGestureRecognizer)
    {
        ProfilePicTap()
    }
   
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {

        if indexPath.row == 1{
            let StoryBord = UIStoryboard.init(name:"Main2", bundle: nil)
            let HomeViewControlle = StoryBord.instantiateViewController(withIdentifier: "HomeVC")as! HomeVC
           // HomeViewControlle.isFromDrawer = true
            self.slideMenuController()?.closeLeft()
            let objNavVC = UINavigationController(rootViewController: HomeViewControlle)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
            
        }
        if indexPath.row == 2 {
            let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
            let MyActivitesViewControlle = StoryBord.instantiateViewController(withIdentifier: "MyActivitesVC")as! MyActivitesVC
            let objNavVC = UINavigationController(rootViewController: MyActivitesViewControlle)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
        }
        if indexPath.row == 3 {
            ProfilePicTap()
        }
        if indexPath.row == 4 {
            let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
            let AboutVC = StoryBord.instantiateViewController(withIdentifier: "AboutAsVC")as! AboutAsVC
            
            let objNavVC = UINavigationController(rootViewController: AboutVC)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
        }
        if indexPath.row == 5 {
           
            let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
            let notifiVC = StoryBord.instantiateViewController(withIdentifier: "NotificationVC")as! NotificationVC
            
            let objNavVC = UINavigationController(rootViewController: notifiVC)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
            
            
        }
        if indexPath.row == 6 {
            let StoryBord = UIStoryboard.init(name:"Main2", bundle: nil)
            let LoginVC = StoryBord.instantiateViewController(withIdentifier: "LoginViewController")as! LoginViewController
            Pref.setAnyObject(false as AnyObject, forKey: kISLogInUser)
            
            let objNavVC = UINavigationController(rootViewController: LoginVC)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
        }
       
        
    }
    func ProfilePicTap(){
        let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
        let ChangePasswordViewControlle = StoryBord.instantiateViewController(withIdentifier: "ChangePasswordVC")as! ChangePasswordVC
        
        let objNavVC = UINavigationController(rootViewController: ChangePasswordViewControlle)
        objNavVC.setNavigationBarHidden(true, animated: true)
        self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
    }
    //MARK:-other Methdo
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }

}
========================================================================================================================

class LeftDrawerVC: UIViewController,UITableViewDelegate,UITableViewDataSource,UIGestureRecognizerDelegate {

    @IBOutlet weak var tblMenu: UITableView!
    let arrayTitles = ["","MY CUSTOMER","MY ACTIVITIES","CHANGE PASSWORD","ABOUT US","NOTIFICATION","LOGOUT"]
    let ArrayImage = ["","menu_my_customer","menu_my_activites","menu_edit_profile","menu_about_us","menu_notification","menu_logout"]
    override func viewDidLoad() {
        super.viewDidLoad()
  
    }
    override func viewWillAppear(_ animated: Bool) {
        super.viewWillAppear(animated)
        self.tblMenu.reloadData()
    }
    var mainVC = UIViewController()
    
    //MARK:-tableView Controller method
    func tableView(_ tableView: UITableView, heightForRowAt indexPath: IndexPath) -> CGFloat {
        if (indexPath as NSIndexPath).row == 0 {
            return 190
        }
        else if indexPath.row == arrayTitles.count{
            return 45
        }
        return 45
    }
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return arrayTitles.count
    }
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        if indexPath.row == 0 {
            let cellHeaders : MenuCell = tableView.dequeueReusableCell(withIdentifier: "HeaderCell") as! MenuCell
            
            
            let tapGestureRecognizer = UITapGestureRecognizer(target: self, action: #selector(imageTapped(tapGestureRecognizer:)))
            cellHeaders.ImgProfile.isUserInteractionEnabled = true
            cellHeaders.ImgProfile.addGestureRecognizer(tapGestureRecognizer)
            let FullName = Pref.getObjectForKey(KprofileName)
            cellHeaders.lblProfileName.text = FullName as? String
            cellHeaders.ImgProfile.layer.cornerRadius = cellHeaders.ImgProfile.bounds.size.height/2
            cellHeaders.ImgProfile.layer.borderWidth = 1.5
            cellHeaders.ImgProfile.layer.borderColor = UIColor.white.cgColor
            cellHeaders.ImgProfile.clipsToBounds = true
            
           
        
            return cellHeaders
        }
        else {
            let cell: MenuCell = tableView.dequeueReusableCell(withIdentifier: "Cell") as! MenuCell
            cell.imgMenu.image = UIImage(named:ArrayImage[indexPath.row])
            cell.lblmenuName.text = arrayTitles[indexPath.row]
            return cell
        }
    }
    func imageTapped(tapGestureRecognizer: UITapGestureRecognizer)
    {
        ProfilePicTap()
    }
   
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {

        if indexPath.row == 1{
            let StoryBord = UIStoryboard.init(name:"Main2", bundle: nil)
            let HomeViewControlle = StoryBord.instantiateViewController(withIdentifier: "HomeVC")as! HomeVC
           // HomeViewControlle.isFromDrawer = true
            self.slideMenuController()?.closeLeft()
            let objNavVC = UINavigationController(rootViewController: HomeViewControlle)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
            
        }
        if indexPath.row == 2 {
            let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
            let MyActivitesViewControlle = StoryBord.instantiateViewController(withIdentifier: "MyActivitesVC")as! MyActivitesVC
            let objNavVC = UINavigationController(rootViewController: MyActivitesViewControlle)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
        }
        if indexPath.row == 3 {
            ProfilePicTap()
        }
        if indexPath.row == 4 {
            let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
            let AboutVC = StoryBord.instantiateViewController(withIdentifier: "AboutAsVC")as! AboutAsVC
            
            let objNavVC = UINavigationController(rootViewController: AboutVC)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
        }
        if indexPath.row == 5 {
           
            let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
            let notifiVC = StoryBord.instantiateViewController(withIdentifier: "NotificationVC")as! NotificationVC
            
            let objNavVC = UINavigationController(rootViewController: notifiVC)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
            
            
        }
        if indexPath.row == 6 {
            let StoryBord = UIStoryboard.init(name:"Main2", bundle: nil)
            let LoginVC = StoryBord.instantiateViewController(withIdentifier: "LoginViewController")as! LoginViewController
            Pref.setAnyObject(false as AnyObject, forKey: kISLogInUser)
            
            let objNavVC = UINavigationController(rootViewController: LoginVC)
            objNavVC.setNavigationBarHidden(true, animated: true)
            self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
        }
       
        
    }
    func ProfilePicTap(){
        let StoryBord = UIStoryboard.init(name:"ProductDetaileMain", bundle: nil)
        let ChangePasswordViewControlle = StoryBord.instantiateViewController(withIdentifier: "ChangePasswordVC")as! ChangePasswordVC
        
        let objNavVC = UINavigationController(rootViewController: ChangePasswordViewControlle)
        objNavVC.setNavigationBarHidden(true, animated: true)
        self.slideMenuController()?.changeMainViewController(objNavVC, close: true)
    }
    //MARK:-other Methdo
    override func didReceiveMemoryWarning() {
        super.didReceiveMemoryWarning()
    }

}
=================================
{

    var window: UIWindow?
    
    //Appdelegate Object
    static let shared = UIApplication.shared.delegate as! AppDelegate
    var customerBean = CustomerBean()
    var arrQuestion = [[String: Any]]()

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplicationLaunchOptionsKey: Any]?) -> Bool {
        //StatesBar
        UIApplication.shared.statusBarView?.backgroundColor = COLOR_COMMON_DARK_ORNAGE
        
        let timeStampSiceNow = Int((Date().timeIntervalSince1970 * 1000.0).rounded())
        print(timeStampSiceNow)
        
        
        window = UIWindow(frame: UIScreen.main.bounds)
        appDelegate.window?.backgroundColor = COLOR_COMMON_DARK_ORNAGE
        
        
        let storybord = UIStoryboard.init(name: "Main2", bundle: nil)
        var mainViewController = UIViewController()
       
        if let Is_LogIn = Pref.getObjectForKey(kISLogInUser) as? Bool
        , Is_LogIn == true {
            mainViewController = (storybord.instantiateViewController(withIdentifier: "HomeVC") as? HomeVC)!
        } else {
            mainViewController = (storybord.instantiateViewController(withIdentifier: "LoginViewController") as? LoginViewController)!
        }
            
        
        let leftViewController = UIStoryboard.init(name: "ProductDetaileMain", bundle: nil).instantiateViewController(withIdentifier: "LeftDrawerVC") as? LeftDrawerVC
        
        let nvc: UINavigationController = UINavigationController(rootViewController: mainViewController)
        nvc.setNavigationBarHidden(true, animated: true)
        
        leftViewController?.mainVC = nvc
        
        let slideMenuController = ExSlideMenuController(mainViewController:nvc, leftMenuViewController: leftViewController!)
        slideMenuController.automaticallyAdjustsScrollViewInsets = true
        
        self.window?.backgroundColor = UIColor.white
        self.window?.rootViewController = slideMenuController
        
        application.isStatusBarHidden = false
        self.window?.makeKeyAndVisible()
        
        INITIAL_SETUP()
        return true
    }
    
   
   

}
