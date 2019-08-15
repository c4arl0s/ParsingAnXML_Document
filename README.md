# ParsingAnXML_Document

ParsingAnXML_Document

- XML is similar to JSON, but instead of key/value pairs it uses tags, like HTML.
- The difference between XML and HTML is that the tags use custom names, so every tag is defined by the developer and may represent an specific   value.

Foundation provides the XMLParser class to create an XML parser. 

``` swift
//
//  ViewController.swift
//  ParsingAnXML_Document
//
//  Created by Carlos Santiago Cruz on 8/14/19.
//  Copyright © 2019 Carlos Santiago Cruz. All rights reserved.
//

import UIKit

class ViewController: UIViewController, XMLParserDelegate {

    override func viewDidLoad() {
        super.viewDidLoad()
        
        let webURL = URL(string: "https://query.yahooapis.com/v1/public/yql?q=select%20item.condition%20from%20weather.forecast%20where%20woeid%20%3D%202487889&format=xml&env=store%3A%2F%2Fdatatables.org%2Falltableswithkeys")
        
        if let parser = XMLParser(contentsOf: webURL!)
        {
            parser.delegate = self
            parser.parse()
        }
    }
    
    func parser(_ parser: XMLParser, didStartElement elementName: String, namespaceURI: String?, qualifiedName qName: String?, attributes attributeDict: [String : String] = [:]) {
        if elementName == "yweather:condition" {
            print(attributeDict["temp"]!)
        }
    }
}
```






