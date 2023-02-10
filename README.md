# axmol-arabic-renderer
Single-Header Arabic Text Renderer Shaping Engine for axmol/cocos2dx in C++

<!-- GETTING STARTED -->
## Getting Started

### Installation

* Put the `ShapingEngine.hpp` file anywhere in your c++ project.
* Include the `ShapingEngine.hpp` file and everything will be under `ShapingEngine` Namespace
* There are arabic fonts you can try in the `arabic-fonts` folder
* There are also pixel art fonts!

<!-- USAGE EXAMPLES -->
## Usage
* Create a new `std::wstring` object containing `utf16` text.
* Call the function `ShapingEngine::render(your_wstring)`, a narrowed `std::string` will be returned that displays arabic letters correctly with the correct vowels too!

## Example
```cpp
std::wstring str = L"السَلامُ عَليكُمْ ورَحْمَةُ اللّهِ وبَركَاتُهْ";
auto label = Label::createWithTTF(ShapingEngine::render(str, false), "bitsy-font-with-arabic.ttf", 20);
```
* Without using `ShapingEngine::render()`:
  
  ![image](https://user-images.githubusercontent.com/45469625/217661761-311c73a1-d108-416b-a328-72b8e8963a7d.png)

* Using ✨ `ShapingEngine::render()` ✨ :
  
  ![image](https://user-images.githubusercontent.com/45469625/217661940-c021e8f8-2c8d-4d2e-909b-b0a416cf5bd7.png)

* The second optinal parameter in `ShapingEngine::render()` is called `render_with_symbols` which simply treats the charachters `<>(){}[]~!@#$%^&*?"':;` as arabic characters, this makes it easier to write arabic text inside parantheses, number ordering, and so much more!
  
* render_with_symbols set to `false`

  ![image](https://user-images.githubusercontent.com/45469625/217662639-279caa8b-4f96-40e1-afcc-4a149414ecd6.png)
  
* render_with_symbols set to `true`

  ![image](https://user-images.githubusercontent.com/45469625/217662746-989f42a3-3d3c-4dbc-9aef-e48bfeb4200b.png)

* You can also try other fonts! like this pixel art font:
  
  ![image](https://user-images.githubusercontent.com/45469625/217663084-c52fd5fd-9c38-4836-8955-c208897692c0.png)

* All these cool fonts and more are in the `arabic-fonts` folder in this repo, Enjoy! :D

* This also supports mixed languages (english and arabic) and also newlines!

  ![image](https://user-images.githubusercontent.com/45469625/217664517-3c532be0-da5c-4710-a61d-235c0b5385aa.png)
  
  ![image](https://user-images.githubusercontent.com/45469625/217664851-bd85887e-90d4-4845-86da-e52111b1b413.png)

* You can make pixel art fonts look crespier by calling `label->getFontAtlas()->setAliasTexParameters();`

  ![image](https://user-images.githubusercontent.com/45469625/217704180-7ffb0560-9f84-433b-8236-dbc9036b219f.png)

* If you want to render multiline arabic text or text that contains numbers you need to use the `ShapingEngine::render_wrap()`, NOTE: for multilines unfortunetly it doesn't work with `setDimension` and overflow texts in general, that's why `render_wrap` needs to be used.

```cpp
label = Label::createWithTTF("", "bitsy-font-with-arabic.ttf", 20);
label->setVerticalAlignment(TextVAlignment::TOP);
label->setHorizontalAlignment(TextHAlignment::RIGHT);
label->getFontAtlas()->setAliasTexParameters();
label->setColor(Color3B(255, 255, 255));


std::wstring str = L"هذا نص طويل جدًا لن يقرأه أحد ويركز عليه ، ويستخدم بشكل أساسي للاختبار ، النص لا يزال مستمراً ... سأقوم بالعد تنازلياً 3 2 1";
std::string arText = ShapingEngine::render_wrap(label->getTTFConfig(), str, true, 340);
```

* The first parameter for `render_wrap` is a ttf config file coming from a label, this is so the function can tell what glyphs have what size and wrap multilines accordingly
* seond parameter is your favourite string!
* third is whether to use symbols or not.
* and fourth is for horizontal wrap size in pixels, this will make sure that the text never exceeds that, if it does then it moves the rest to a new line and so on.

* This is a text rendered in multilines:

     ![image](https://user-images.githubusercontent.com/45469625/218175516-11a7edf9-cb8c-44ba-b8eb-e09fadb95dff.png)



* Notice how the numbers are in correct order! (I said I would do a count down in arabic)
* If you want arabic numbers you can call the `ShapingEngine::arabify_numbers();`

```cpp
label->setString(ShapingEngine::arabify_numbers(arText));
```

   ![image](https://user-images.githubusercontent.com/45469625/218175557-7b45bfc9-b03e-4a41-900a-de0c14ff3527.png)

* Text scrolling, Unfortunately `std::string.substr` doesn't work with arabic text but `ShapingEngine::substr()` can be used instead, it takes a string and count, This is different from your typical substr because it it scrolls from right to left (not left to right like `std::string.substr` does)

```cpp
void HelloWorld::update(float dt)
{
    auto str1 = ShapingEngine::substr(arText, (int)currentIndex++);
    label->setString(ShapingEngine::arabify_numbers(str1));
}
```

<!-- CONTRIBUTING -->
## Contributing

* Contribute and add your own language! or you can improve upon this implmentation, **greatly appreciated**.

* If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue.
Don't forget to give the project a star! Thanks again!

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>
