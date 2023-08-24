public:: true
date:: "2022-01-19"
tags:: DevOps

- **例子**
- ```python
  import argparse
  
  parser = argparse.ArgumentParser(description='help')
  parser.add_argument('-f', dest='frst', type=int, help='开始编号')
  parser.add_argument('-c', dest='cookies', type=str, help='osu登录cookies. e.g. -c "cookiess"')
  args = parser.parse_args()
  
  print(args.frst)
  ```
- **[[Python]]封装应用程序**
- `pip install pyinstaller` https://pyinstaller.org/en/stable/usage.html
- `pyinstaller myscript.py -F -i NONE -n myscript`
- **依赖信息**
- `pip freeze > requirements.txt`
- `pip install -r requirements.txt`