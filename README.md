# axmol-arabic-renderer
Single-Header Arabic Text Renderer Shaping Engine for axmol/cocos2dx in C++

<!-- GETTING STARTED -->
## Getting Started

### Installation

* Put the `ShapingEngine.hpp` file anywhere in your c++ project.
* There are arabic fonts you can try in the `arabic-fonts` folder
* There are also pixel art fonts!

<!-- USAGE EXAMPLES -->
## Usage
* Create a new `std::wstring` object containing `utf16` text.
* Call the function `ShapingEngine::render(your_wstring)`, a narrowed std::string will be returned that displays arabic letters correctly with the correct vowels too!

## Example
```cpp
std::wstring str = L"السَلامُ عَليكُمْ ورَحْمَةُ اللّهِ وبَركَاتُهْ";
auto label = Label::createWithTTF(ShapingEngine::render(str), "bitsy-font-with-arabic.ttf", 20);
```
* Without using `ShapingEngine::render()`: ![image](https://user-images.githubusercontent.com/45469625/217660241-6f82050e-1984-4f41-a1bf-e5493499b1ca.png)


<!-- CONTRIBUTING -->
## Contributing

* Contribute and add your own language! or you can improve upon this implmentation, **greatly appreciated**.

* If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue.
Don't forget to give the project a star! Thanks again!

<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>
