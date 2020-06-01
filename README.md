# ARVirtl
POD for showing AR based location points



... info about ARVirtlo


Requirements
ARKit requires iOS 12, and supports the following devices:

iPhone 6S and upwards
iPad (2017)
All iPad Pro models
iOS 12 can be downloaded from Apple’s Developer website.

Usage
This library contains the ARVirtlo framework, as well as a demo application.

Building with Swift:

Add to your podfile:
pod 'ARVirtlo'

In Terminal, navigate to your project folder, then:

pod install

Add NSCameraUsageDescription and NSLocationWhenInUseUsageDescription to plist with a brief explanation (see demo project for an example)

Quick start guide:

Change your Initial ViewController to this:


//
//  ViewController.swift
//  Demo
//
//  Created by Ishkhan Gevorgyan on 2/18/20.
//  Copyright © 2020 Ishkhan Gevorgyan. All rights reserved.
//

import UIKit
import ARVirtlo

class ViewController: UIViewController, VitloVCDelegate {
   
     open var tableData = [VirtloProperty]()
     open var serverPlaces = [VirtloProperty]()
    

    override func viewDidLoad() {
        
        LocationManager.sharedInstance.checkStatus()
       
       
        
        super.viewDidLoad()
        self.view.backgroundColor = .red
        
        let button = UIButton(frame: CGRect(x: 100, y: 100, width: 100, height: 50))
         button.backgroundColor = .green
         button.setTitle("Test Button", for: .normal)
         button.addTarget(self, action: #selector(buttonAction), for: .touchUpInside)

         self.view.addSubview(button)
    
        
    }
    override func viewDidAppear(_ animated: Bool) {
        
         LocationManager.sharedInstance.start()
    }
    
    @objc func buttonAction(sender: UIButton!) {
        let prop:VirtloProperty = VirtloProperty()
               prop.lat = (LocationManager.sharedInstance.latestLocation?.coordinate.latitude)! + 0.000001
               prop.lng = (LocationManager.sharedInstance.latestLocation?.coordinate.longitude)! + 0.000001
               prop.name = "Apartment"
               prop.category_color = "#00ADFA"
               prop.category_id = 1000
               tableData.append(prop)
               serverPlaces.append(prop)
                let prop4:VirtloProperty = VirtloProperty()
               prop4.lat = 40.212314
                      prop4.lng = 44.489013
                      prop4.name = "erkrord Ket"
                      prop4.category_color = "#00ADFA"
              // prop4.logo = "https://virtlo.com//uploads/places/39/39/5cioemhphv9mnm571fcsr2kya.png"
                prop4.category_id = 1000
                      tableData.append(prop4)
                      serverPlaces.append(prop4)
               
               let prop2:VirtloProperty = VirtloProperty()
               prop2.lat = 40.222314
                      prop2.lng = 44.479013
                      prop2.name = "errord Ket"
                      prop2.category_color = "#0037CE"
                      prop2.rand_position = 1300
                      prop2.category = "Man-made"
                      prop2.parent_category_title = "Nature"
                     
                      prop2.category_id = 1000
                      prop2.opening_hours = "Mo-Su 09:00 - 18:00"
               
             
                      tableData.append(prop2)
                      serverPlaces.append(prop2)
               
                let prop3:VirtloProperty = VirtloProperty()
               prop3.lat = 40.252314
                      prop3.lng = 44.499013
                      prop3.name = "chorord Ket"
                      prop3.category_color = "#0037CE"
                      prop3.opening_hours = "Mo-Su 09:00 - 18:00"
                      prop3.street = "22 Vagharshyan, Yerevan"
                       prop3.category_id = 1000
                      tableData.append(prop3)
                      serverPlaces.append(prop3)
        
        let bundle = Bundle(for: VirtloVC.self)
               let storyboard = UIStoryboard(name: "Storyboard", bundle: bundle)
        let controller = storyboard.instantiateViewController(withIdentifier: "VirtloVC") as! VirtloVC
        //controller.tableData = tableData
        //controller.delegate = self
        controller.serverPlaces = serverPlaces
        controller.modalPresentationStyle = .overFullScreen
        
       // controller.isCustomToolTipUsed = true
       
//       controller.firstHintTitle = "firstHintTitle"
//       controller.firstHintDescription1 = "firstHintDescription1"
//       controller.firstHintDescription2 = "firstHintDescription2"
//       controller.firstHintImage = UIImage(named:"testVirtlo")
//       
//       
//       controller.secondHintTitle = "secondHintTitle"
//       controller.secondHintDescription = "secondHintDescription"
//       controller.secondHintTapOrSwipe = "secondHintTapOrSwipe"
//       controller.secondHintRadar = "secondHintRadar"
//       controller.secondHintImage = UIImage(named:"testVirtlo")
//       
//       controller.listHintTitle = "listHintTitle"
//       controller.listHintDescription1 = "listHintDescription1"
//       controller.listHintDescription2 = "listHintDescription2"
//       controller.keepItStright = "keepItStright"
//    controller.listHintImage = UIImage(named:"testVirtlo")
        
        self.present(controller, animated: true, completion: nil)
    }
    
    func openElementDetails(virtloProperty:VirtloProperty)
    {
        let storyboard = UIStoryboard(name: "Main", bundle: .main)
        let controller = storyboard.instantiateViewController(withIdentifier: "SecondViewController") as! SecondViewController
        controller.modalPresentationStyle = .overFullScreen
        controller.virtloProperty = virtloProperty
        self.show(controller, sender: true)
           print("hello")
    }
    
  
    
}



You can see the usage of ARVirtlo by downloading app Virtlo:
https://apps.apple.com/app/id1421135861
