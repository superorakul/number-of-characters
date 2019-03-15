package re;
//добавляем библиотеки для работы с текстовыми полями, метками, для создания графического окна
import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Dimension;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.BoxLayout;
import javax.swing.JButton;
import javax.swing.JComponent;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.JTextField;
import javax.swing.SwingUtilities;
import javax.swing.border.EtchedBorder;

//Главный класс, реализующий интерфейс ActionListener
//Интерфейс нужен для обработки события нажатия на кнопку
public class calculator implements ActionListener{
  JFrame frame = new JFrame("Подсчет количества символов в тексте"); //главное окно
  JPanel panelLeft = new JPanel(); //панель с метками
  JPanel panelRight = new JPanel(); //панель с текстовыми полями
  JPanel panelBottom = new JPanel(); //панель с кнопками
  public JTextField[] fields = new JTextField[2];//массив текстовых полей

  //конструктор
  public calculator() {
      //устанавливаем менеджер компоновки для панели с метками
      //делаем выравнивание по вертикали
      panelLeft.setLayout(new BoxLayout(panelLeft, BoxLayout.Y_AXIS));
      //устанавлиаем  размер 250 на 300 пикселей
      panelLeft.setPreferredSize(new Dimension(250, 300));

      //устанавливаем менеджер компоновки для панели с текстовыми полями
      //делаем выравнивание по вертикали
      panelRight.setLayout(new BoxLayout(panelRight, BoxLayout.Y_AXIS));
      //устанавливаем  размер 130 на 300 пикселей
      panelRight.setPreferredSize(new Dimension(230,300));

      //добавлям метки через метод addLabel
      addLabel(panelLeft, "Текст:", Color.BLACK);
      addLabel(panelLeft, "Количество символов в тексте:", Color.BLACK);
      //добавляем текстовые поля через цикл и записываем их в массив
      for(int i = 0; i < fields.length; i++){
          if(fields.length >= 0){
              //записываем ссылку из метода в массив для дальнейшей работы с текстовым полем
              fields[i] = addTextField(panelRight);}

      }


      //добавляем кнопки расчета и сброса
      JButton calc = addButton(panelBottom, "Расчет");
      //добавляем слушатель на событие нажатия
      calc.addActionListener(this);
      JButton reset = addButton(panelBottom, "Сброс");
      //добавляем слушатель на событие нажатия
      reset.addActionListener(this);


      //делаем главную форму видимой
      frame.setVisible(true);
      //устанавливаем действие при нажатии на крестик - завершение приложения
      frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
      //устанавливаем начальное положение относительно центра экрана (по центру)
      frame.setLocationRelativeTo(null);
      //Устанавливаем размер главного окна(400 на 450)
      frame.setSize(450,200);
      //Добавляем метку с информацией к работе в самый верх окна
      JLabel top = new JLabel("Первое поле является обязательным для заполнения");
      //устанавливаем выравнивание текста в метке по центру
      top.setHorizontalAlignment(JLabel.CENTER);

      //добавляем панели на клавное окно
      frame.add(top, BorderLayout.NORTH);
      frame.add(panelLeft, BorderLayout.WEST);
      frame.add(panelRight, BorderLayout.EAST);
      frame.add(panelBottom, BorderLayout.SOUTH);
      frame.setResizable(false); //запрещаем изменение размеров главного окна

  }


  //метод добавления текстовых меток
  public void addLabel(JComponent container, String name, Color color){
      //создаем тестовую метку с именем name
      JLabel label = new JLabel(name);
      //устанавливаем максимально допустимый размер
      label.setMaximumSize(new Dimension(200,20));
      //устанавливаем цвета текста
      label.setForeground(color);
      //устанавливаем выравнивание по правому краю
      label.setHorizontalAlignment(JLabel.RIGHT);
      //добавляем рамку
      label.setBorder(new EtchedBorder());
      //Добавляем текстовую метку в панель
      container.add(label);
  }

  //метод добавления текстовых полей
  public JTextField addTextField(JComponent container){
      //Создаем текстовое поле
      JTextField field = new JTextField();
      //устанавливаем его максимально допустимый размер
      field.setMaximumSize(new Dimension(350,20));
      //добавляем текстовое поле на панель
      container.add(field);
      //возвращаем ссылку на текстовое поле
      return field;
  }

  //метод добавления кнопок
  public JButton addButton(JComponent container, String name){
      //Создаем кнопку
      JButton button = new JButton(name);
      //Устанавливаем максимально допустимый размер
      button.setMaximumSize(new Dimension(100,20));
      //Выравниваем по горизонтали по центру
      button.setHorizontalAlignment(JButton.CENTER);
      //добавляем кнопку на панель
      container.add(button);
      //возвращаем ссылку на кнопку
      return button;
  }


  //метод подсчета
  public void calculate() throws Exception {
  	String getText = fields[0].getText();
      String valueOf = String.valueOf(getText.length());
      fields[1].setText(valueOf);
  }
         

  //Метод обработки события нажатия на кнопку
  @Override
  public void actionPerformed(ActionEvent e) {
      //узнаем имя кнопки, на которую нажали
      if (e.getActionCommand().equals("Расчет")) {
          try {
              //выполняем расчет
              calculate();
          } catch (Exception ex) {
              JOptionPane.showMessageDialog(null, "Проверьте правильность ввода");
          }
      }else{
          //очищаем все поля
          for(int i=0; i<fields.length; i++){
              fields[i].setText("");
          }
      }
  }
  
  
  public static void main(String[] args) {
      SwingUtilities.invokeLater(new Runnable() {
          @Override
          public void run() {
              new calculator();
          }
      });
  }

}
