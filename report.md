# Отчёт о тестировании Credit Card Number Validator

Краткое описание

24.11.2021 - 24.11.2021 было проведено тестирование Credit Card Number Validator

На тестирование затрачено: 10 мин.

В результате тестирования выявлены следующие дефекты:

[Не проходят валидацию карты с количеством цифр в номере <16](https://github.com/Katriona17/Java1.2/issues/1)

# Описание процесса 

В процессе тестирования использовались следующие артефакты:

[баг-репорт](https://github.com/Katriona17/Java1.2/issues/1)


В качестве тестовых данных использовались данные Java:

```Java
public class Main {
    public static void main(String[] args) {
        // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
        String number = "36257627049764";
        System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
    }

    public static boolean isValidCardNumber(String number) {
        if (number == null) {
            return false;
        }

        if (number.length() != 16) {
            return false;
        }

        long result = 0;
        for (int i = 0; i < number.length(); i++) {
            int digit;
            try {
                digit = Integer.parseInt(number.charAt(i) + "");
            } catch (NumberFormatException e) {
                return false;
            }

            if (i % 2 == 0) {
                digit *= 2;
                if (digit > 9) {
                    digit -= 9;
                }
            }
            result += digit;
        }

        return (result != 0) && (result % 10 == 0);
    }
}
```


Тестирование производилось в следующем окружении:

1. Windows 10 Pro 64-разрядная операционная система, процессор x64
1. JDK 11.0.12
