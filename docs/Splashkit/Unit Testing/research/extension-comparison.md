# CMake Tools
- Author: Microsoft
- https://marketplace.visualstudio.com/items?itemName=ms-vscode.cmake-tools
- https://github.com/microsoft/vscode-cmake-tools

This extension will require some changes to the project's CMakeLists.txt for the CTest integration to work.
The developer Catch2 recommends CMake integration anyway, and it's a fairly simple change, just a few lines:

```
include(CTest)
include("${CMAKE_CURRENT_SOURCE_DIR}/catch/Catch.cmake")
catch_discover_tests(skunit_tests)
```

CMake Tools also has integration with VS Code's coverage feature, opening another useful feature up for future
consideration. This highlights lines that have run in testing and also shows a summary of code coverage for the whole
project.

Due to the way it reads tests from CTest, it doesn't allow you to click a test to go straight to its line in code,
and the tests are structured in a flat list. A tree review requires renaming the tests themselves with delmiters that
the extension can read, for example "utilities/is_prime".

# C++ Test Mate
- Author: Mate Pek
- https://marketplace.visualstudio.com/items?itemName=matepek.vscode-catch2-test-adapter
- https://github.com/matepek/vscode-catch2-test-adapter

Can pick up tests without them being registered with CTest, meaning no changes to CMakeLists.txt is necessary.
There's the ability to click on a test to go directly to its line of code, and the extension can be configured to
parse tests so that the list is nicely organised (for example, grouping by source code file), without requiring
changes to test names.

Doesn't currently have a coverage feature, so that would have to be done via a separate extension.
https://github.com/matepek/vscode-catch2-test-adapter/issues/433
Gcov viewer is an option for this, but isn't as nicely integrated with VS Code, and doesn't have a nice coverage summary.
https://marketplace.visualstudio.com/items?itemName=JacquesLucke.gcov-viewer 


Currently has a problem with Catch2 2.x (which we use), where test names greater than 80 characters fail to get run.
https://github.com/matepek/vscode-catch2-test-adapter/issues/21
This seems to have been fixed in Catch2 3.x but that would require addressing some breaking changes in the upgrade
from 2.x.