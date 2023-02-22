## Pyside6

- Установка приложения

```python
python -m venv venv
venv\Scripts\activate
pip install pyside6
```

- Проверяем установку

```python
import PySide6.QtCore

# Prints PySide6 version
print(PySide6.__version__)

# Prints the Qt version used to compile PySide6
print(PySide6.QtCore.__version__)
```

- Создаем приложение

```python
import sys  #предоставляет функции для управления средой выполнения Python
from PySide6 import QtCore, QtWidgets, QtGui  #основные модули

class MyWidget(QtWidgets.QWidget):
    def __init__(self):
        super().__init__()

        self.hello = ['Привет мир']

        self.button = QtWidgets.QPushButton('Click me!')
        self.text = QtWidgets.QLabel('Hello World',
                                     alignment=QtCore.Qt.AlignCenter)

        self.layout = QtWidgets.QVBoxLayout(self)
        self.layout.addWidget(self.text)
        self.layout.addWidget(self.button)

        self.button.clicked.connect(self.magic)

    @QtCore.Slot()
    def magic(self):
        self.text.setText(random.choice(self.hello))

if __name__ == "__main__":
    app = QtWidgets.QApplication([])

    widget = MyWidget()
    widget.resize(800, 600)
    widget.show()

    sys.exit(app.exec())
```

**QtCore** - предоставляет основные функции, не связанные с графическим интерфейсом, такие как сигналы и слоты, свойства, базовые классы моделей элементов, сериализация и многое другое
`import PySide6.QtCore`

**QtGui** - функции графического интерфейса: события, окна и экраны, OpenGL и растровое 2D-рисование, а также изображения
`import PySide6.QtGui`

**QtWidgets** - предоставляет готовые к использованию виджеты для вашего приложения, включая графические элементы для вашего пользовательского интерфейса
`import PySide6.QtWidgets`

```python
from PyQt6.QtWidgets import QApplication, QMainWindow, QPushButton 
#Основные модули для Qt: QtWidgets, QtGui и QtCore.

import sys # Только для доступа к аргументам командной строки 

# Подкласс QMainWindow для настройки главного окна приложения
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()

        self.setWindowTitle("My App")

        button = QPushButton("Press Me!")

        self.setFixedSize(QSize(400, 300))

        # Устанавливаем центральный виджет Window.
        self.setCentralWidget(button)

# Приложению нужен один (и только один) экземпляр QApplication.
# Передаём sys.argv, чтобы разрешить аргументы командной строки для приложения.
# Если не будете использовать аргументы командной строки, QApplication([]) тоже работает

app = QApplication(sys.argv)

# Создаём виджет Qt — окно.
window = MainWindow()
window.show()  # Важно: окно по умолчанию скрыто.

# Запускаем цикл событий.
app.exec()

```

- Запускаем приложение `python app.py`
- Посмотреть превью приложения `CTR + R`

---

- ****Конвертируем файл ресурсов и интерфейса****
нужно написать в терминал `pyside6-rcc`, название файла ресурсов, флаг `-o` и название файла на выходе
`pyside6-rcc resources.qrc -o resources.py`

 файл интерфейса конвертируется таким же образом, только с помощью приложения `pyside6-uic`

 `pyside6-uic main.ui -o ui_main.py`


