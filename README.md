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
* Call the function `ShapingEngine::render(your_wstring)`, a narrowed std::string will be returned that displays arabic letters correctly with the correct vowels too!

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

* All these fonts and more are in the `arabic-fonts` folder in this repo, Enjoy! :D

<!-- CONTRIBUTING -->
## Contributing

* Contribute and add your own language! or you can improve upon this implmentation, **greatly appreciated**.

* If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue.
Don't forget to give the project a star! Thanks again!

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>
