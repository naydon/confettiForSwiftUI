# confettiForSwiftUI
Generate confettis in SwiftUI


To generate the confettis in your SwiftUI view, add the Confetti.swift file in your project, then insert the code below in your ContentView struct:


```Swift
    @State var confettiAnimate = [false]
    @State var confettiFinishedAnimationCouter = 0
    @State var confettiCounter = 0
    @State private var confettiTimer: Timer?
    
    
    
    
    func startConfettiTimer()  {
        confettiTimer = Timer.scheduledTimer(withTimeInterval: 0.05, repeats: true, block: { _ in
            confettiAnimate[confettiCounter].toggle()
            confettiAnimate.append(false)
            confettiCounter+=1
        })
        _ = confettiTimer
    }
    
    func stopConfettiTimer() {
        confettiTimer?.invalidate()
    }
```

Whereever you want the confettis to be displayed, insert the following code in your view :
```Swift
VStack{
    ZStack{
        ForEach(confettiFinishedAnimationCouter...confettiCounter, id:\.self){ i in
            ConfettiContainer(animate:$confettiAnimate[i], finishedAnimationCouter:$confettiFinishedAnimationCouter, num:1)
        }
    }
}
```

And then to run the confettis, call 
```Swift
startConfettiTimer()
```

To stop the confettis, call
```Swift
stopConfettiTimer()
```



Credits:
The code above has been produced based the following extange on stackoverflow:  https://stackoverflow.com/questions/64956392/swiftui-confetti-animation

