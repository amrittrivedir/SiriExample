# SiriExample

#Building a Speech-to-Text App Using Siri in iOS 10.

Since launch of Siri in IOS we are addicted to it and we are loving the powerful recognition power of Siri. But till now we don’t have access to Siri to use in IOS application. But since IOS 10 Siri is available to developer. 
Speech Kit is the framework which Siri uses for speech recognition. There are a handful of speech recognition frameworks available today, but they are either very expensive or simply not as good. In this article we will learn how to use Siri features in our app.

#Core Concept of the app

We will build one simple app to to recognize words from speech kit framework. We will show recognized texts in iPhone device.

#Setting up your environment

To use the Speech framework, you have to first import it and adopt the SFSpeechRecognizerDelegate protocol. So let’s import the framework, and add its protocol to the ViewController class. Now your ViewController.swift should look like this: 

import UIKit
import Speech
 
class ViewController: UIViewController, SFSpeechRecognizerDelegate 
{        
    @IBOutlet weak var textView: UITextView!
    @IBOutlet weak var microphoneButton: UIButton!
    
    override func viewDidLoad() 
    {
        super.viewDidLoad()
        
    }
 
    @IBAction func microphoneTapped(_ sender: AnyObject) 
    {
 
    } 
}

#Handle Authorization

Before using the speech framework for speech recognition, you have to first ask for users’ permission because the recognition doesn’t happen just locally on the iOS device but Apple’s servers. All the voice data is transmitted to Apple’s backend for processing. Therefore, it is mandatory to get the user’s authorization.

    speechRecognizer.delegate = self  //3
    
    SFSpeechRecognizer.requestAuthorization { (authStatus) in  //4
        
        var isButtonEnabled = false
        
        switch authStatus {  //5
        case .authorized:
            isButtonEnabled = true
            
        case .denied:
            isButtonEnabled = false
            print("User denied access to speech recognition")
            
        case .restricted:
            isButtonEnabled = false
            print("Speech recognition restricted on this device")
            
        case .notDetermined:
            isButtonEnabled = false
            print("Speech recognition not yet authorized")
        }

<key>NSMicrophoneUsageDescription</key>
	<string>Your microphone will be used to record your speech when you press the &quot;Start Recording&quot; button.</string>
	<key>NSSpeechRecognitionUsageDescription</key>
	<string>Speech recognition will be used to determine which words you speak into this device&apos;s microphone.</string>

Till now you learned how to set up the Speech kit in your project and it’s basic necessary things. You will find more details in our demo project in github. Please check out it from here.