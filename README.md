# Selenium-Util

本仓库为selenium脚本封装库，利用python装饰器以及闭包思想，致力于更好的调试自动化爬虫，让爬虫技术更好入门，详细使用请查看该仓库的Example.ipynb

函数名中带element下标的皆为用装饰器装饰的函数，可只传入xpath，无element下标的函数与原selenium函数无异，需要先获取元素再将参数传入，以下函数接口文档均为带装饰器函数


| 方法名称                      | 描述                                     | 参数                                                         | 返回                      |
| ----------------------------- | ---------------------------------------- | :----------------------------------------------------------- | ------------------------- |
| ***\*init\****                | 初始化Selenium_Edge类实例。              | `update` (bool): 是否更新WebDriver。 <br> `cookies` (bool): 是否使用cookies。 <br> `cookies_url` (str): 获取cookies的URL。 <br> `proxy_url` (str): 代理服务器URL。 <br> `action` (object): ActionChains对象。 | 无                        |
| **create_driver**             | 初始化并配置Edge WebDriver。             | 无                                                           | WebDriver 对象            |
| **update_driver**             | 检测并更新Edge WebDriver版本。           | 无                                                           | 无                        |
| **get_driver**                | 打开指定URL并可选等待某元素加载。        | `url` (str): 要打开的URL。 <br> `wait_time` (int): 等待时间（秒）。 <br> `wait_element_xpath` (str): 等待元素的XPath。 | 无                        |
| **locate_element**            | 装饰器，用于定位元素并处理异常。         | xpath (str): XPath表达式。<br/><br/>xpath_kind (enum): 用于指定如何查找元素，比如 By.ID, By.XPATH 等。<br/><br/>father_element (WebElement): 可选参数，指定一个父元素，用于在其子元素中进行搜索。若不提供，Selenium将在整个页面进行搜索。<br/><br/>default_value (any): 如果在指定的超时时间内未找到元素，该参数定义了应返回的默认值。这个值可以是任何类型，取决于你希望在找不到元素时如何处理。<br/><br/>timeout (int): 这是等待元素出现的最大时间，单位是秒。如果在这段时间内没有找到元素，根据 default_value 的设置，函数将返回默认值或触发异常。<br/><br/>is_watch (bool): 默认为False。若为 True，则等待元素可见；若为 False，则只检查元素是否存在于DOM中。 | 装饰的函数的返回值        |
| **get_element**               | 获取单个元素。                           | 同上                                                         | WebElement 或默认值       |
| **get_element_text**          | 获取元素文本。                           | 同上                                                         | 文本字符串或默认值        |
| **get_element_attribute**     | 获取网页元素的指定属性值。               | `attribute` (str): 指定要从元素中提取的属性。默认值是 `'href'`，这是超链接元素的URL。可以指定其他如 `'textContent'`、`'innerHTML'` 或 `'outerHTML'` 等属性。 | 无                        |
| **input_element_text**        | 清除输入框内容同时向输入框元素发送文本。 | text（str）:发送的文本内容                                   | 无                        |
| **click_element**             | 点击元素。                               | 同上                                                         | 无                        |
| **locate_elements**           | 装饰器，用于获取元素列表                 | 同locate_element                                             | 装饰的函数的返回值        |
| **get_cookies**               | 获取当前页面的所有cookies并保存到文件。  | 无                                                           | 包含cookies名称和值的字典 |
| **set_cookies**               | 从文件读取cookies并设置到会话。          | 无                                                           | 无                        |
| **destroy**                   | 关闭浏览器并结束会话。                   | 无                                                           | 无                        |
| **switch_to_window_by_index** | 根据窗口索引切换窗口。                   | `index` (int): 窗口索引。                                    | 无                        |
