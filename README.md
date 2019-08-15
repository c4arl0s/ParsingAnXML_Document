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

``` console
2019-08-14 20:47:03.563614-0500 ParsingAnXML_Document[10589:616359] TIC TCP Conn Failed [1:0x6000001392c0]: 12:8 Err(-65554)
2019-08-14 20:47:03.567233-0500 ParsingAnXML_Document[10589:616359] Task <9C0FEFF6-1528-4FE5-8EA7-F643A96578B9>.<0> HTTP load failed (error code: -1003 [12:8])
2019-08-14 20:47:03.568837-0500 ParsingAnXML_Document[10589:616359] NSURLConnection finished with error - code -1003
```


# Fix the code.





