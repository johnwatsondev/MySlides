# React Native 初探<br><sub>by johnwatsondev</sub></br>

---

# Prerequisites

- HTML & CSS
- JavaScript
Some ES6 Feature: arrow function/classes/let/const

- React 
props/state/lifting state up/JSX

- Tips
Please check **Official Doc** or use **Google** to comprehend these concepts

---

# Quiz

```javascript
class DisplayText extends React.Component {
    render() {
        let displayText = this.props.isFamiliarBasicConcepts ? 'Let\'s go baby~' : 'Go home please.';
        return (
            <View style={{flex: 1, flexDirection: 'column'}}>
                <Text>{displayText}</Text>
            </View>
        );
    }
}
```

---

# Result - Positive

![inline](https://user-images.githubusercontent.com/12760754/27515763-b56c7b06-59dd-11e7-826f-20df8905f817.png)

---

# Result - Negative

![inline](https://camo.githubusercontent.com/bd9052cb8a5713d0ff354dfb8ab52dacdfd057c4/687474703a2f2f7777342e73696e61696d672e636e2f6c617267652f3565396138316462677731657539306d30387638366a323064773039613379752e6a7067)

---

# What

* **Learn once, write anywhere**

* Build native mobile apps using **JavaScript** and **React**

---

# Talk is cheap

```javascript, [.highlight: 1,12-16,18-20,21]
class DisplayText extends React.Component {
    _renderPicture() {
        let picUrl = 'dummyImgUrl';
        if (!this.props.isFamiliarBasicConcepts) {
            return (
                <Image style={{width: 200, height: 100}} source={{uri: picUrl}} resizeMode='stretch'/>
            );
        } else {
            return null;
        }
    }
    render() {
        let displayText = this.props.isFamiliarBasicConcepts ? 'Let\'s go baby~' : 'Go home please.';
        return (
            <View style={{flex: 1, flexDirection: 'column'}}>
                <Text>{displayText}</Text>
                {this._renderPicture()}
            </View>
        );
    }
}
```

---

# Talk is cheap

```javascript
class DisplayText extends React.Component {
    _renderPicture() {
        let picUrl = 'dummyImgUrl';
        if (!this.props.isFamiliarBasicConcepts) {
            return (
                <Image style={{width: 200, height: 100}} source={{uri: picUrl}} resizeMode='stretch'/>
            );
        } else {
            return null;
        }
    }
    render() {
        let displayText = this.props.isFamiliarBasicConcepts ? 'Let\'s go baby~' : 'Go home please.';
        return (
            <View style={{flex: 1, flexDirection: 'column'}}>
                <Text>{displayText}</Text>
                {this._renderPicture()}
            </View>
        );
    }
}
```

---

# Getting value from the outer world

```javascript
class DisplayText extends React.Component {
    _renderPicture() {
        let picUrl = 'dummyImgUrl';
        if (!this.props.isFamiliarBasicConcepts) {
            return (
                <Image style={{width: 200, height: 100}} source={{uri: picUrl}} resizeMode='stretch'/>
            );
        } else {
            return null;
        }
    }
    render() {
        let displayText = this.props.isFamiliarBasicConcepts ? 'Let\'s go baby~' : 'Go home please.';
        return (
            <View style={{flex: 1, flexDirection: 'column'}}>
                <Text>{displayText}</Text>
                {this._renderPicture()}
            </View>
        );
    }
}
```

---

# Getting value from the outer world

```javascript, [.highlight: 4,13]
class DisplayText extends React.Component {
    _renderPicture() {
        let picUrl = 'dummyImgUrl';
        if (!this.props.isFamiliarBasicConcepts) {
            return (
                <Image style={{width: 200, height: 100}} source={{uri: picUrl}} resizeMode='stretch'/>
            );
        } else {
            return null;
        }
    }
    render() {
        let displayText = this.props.isFamiliarBasicConcepts ? 'Let\'s go baby~' : 'Go home please.';
        return (
            <View style={{flex: 1, flexDirection: 'column'}}>
                <Text>{displayText}</Text>
                {this._renderPicture()}
            </View>
        );
    }
}
```

---

# Storing value in your inner world

```javascript
class MyInput extends React.Component {
    constructor() {
        super();
        this.state = {inputText: ''}
    }
    render() {
        return (
            <View style={{marginHorizontal: 40}}>
                <TextInput style={{alignSelf: 'stretch', height: 40}}
                           placeholder="Please input here!"
                           onChangeText={text => {
                               console.log("MyInput onChangeText = " + text);
                               this.setState({inputText: text});
                           }}/>
                <Text>{`Your inputText is ${this.state.inputText}`}</Text>
            </View>
        );
    }
}
```

---

# Storing value in your inner world

```javascript, [.highlight: 4,13]
class MyInput extends React.Component {
    constructor() {
        super();
        this.state = {inputText: ''}
    }
    render() {
        return (
            <View style={{marginHorizontal: 40}}>
                <TextInput style={{alignSelf: 'stretch', height: 40}}
                           placeholder="Please input here!"
                           onChangeText={text => {
                               console.log("MyInput onChangeText = " + text);
                               this.setState({inputText: text});
                           }}/>
                <Text>{`Your inputText is ${this.state.inputText}`}</Text>
            </View>
        );
    }
}
```

---

# Props vs State

Only give props if your data is not going to change over time/in response to user interaction

---

# We can build a completed RN App now

- Text, Image
- Button, TextInput, Switch
- Picker, Slider, SectionList, StatusBar
- View, FlatList, ListView, ScrollView, WebView, etc

---

# Is that enough<br>in production environment?</br>

![inline](https://user-images.githubusercontent.com/12760754/27595159-7a61d544-5b8e-11e7-90a0-e24fc3c978ee.jpeg)

---

# Hybrid App

- Part Native
- Part React Native

## What's the most important thing?

---

# Communication between JS and Native

- Native Module
- JS Module
- InitialProps

---

# Native Module

## JS side 
### invoke
## Native code

---

# JS Module

## Native side
### invoke
## JS code

---

# InitialProps

Native code pass any value as props to the React Native Component

- Bonus: We can invoke **different** React Native Page from the **same native entry**(Activity/UIViewController).

---

# How to communicate?

![inline 86%](https://user-images.githubusercontent.com/12760754/27598411-fc98c24e-5b97-11e7-80da-bca9cb3b7536.jpeg)

### Indirectly | No-Blocked

---

# How to communicate?

![inline](https://user-images.githubusercontent.com/12760754/27597979-a7f2c600-5b96-11e7-9b99-9f139ff14a33.jpeg)

### Asynchronous | Batched Message | Serializable

---

# How to communicate?

### Please dive into the source code <br>to get more details. :sunglasses::smiling_imp::joy:</br>

---

# React → React Native

- React _**forces**_ us to break our applications down into _**discrete components**_, each representing a single view.

- React _**raises the level of abstraction and simplifies the programming model**_.

- Code is more predictable. (credit: JSX)

---

# Efficient Tools

- WebStrom (Keymap, Live Templates)
- Shell Scripts (Debugging, Build Artifacts)
- Vysor (Just For Android Physical Device)

---

# More Resource

![inline](https://github.com/johnwatsondev/InterestingImageForSlide/raw/master/LoveToLearn/I%20want%20to%20learn%201.jpeg)

- [Awesome React Native](http://www.awesome-react-native.com/)
- [More Resource](http://facebook.github.io/react-native/releases/0.46/docs/more-resources.html)

---

# Question

---

# Homework

请各位同学自己搭建一套 RN 环境，成功运行 HelloWorld。  
心有余力的同学可以重构下现有业务界面。

---

# Thanks
