# SchoolClass

```bash
function School(name, minYears) {
  if (!name) {
    throw Error("Не указано название школы");
  }

  if (!minYears) {
    throw new Error("Не указано минимальное количество лет");
  }

  const MIN_YEARS = minYears;
  const SCHOOL_NAME = name;

  this.checkAge = function (age) {
    if (age < MIN_YEARS) {
      return {
        result: false,
        message: `Вам запрещено водить авто, вам должно быть ${MIN_YEARS} лет или больше`,
      };
    } else if (age >= MIN_YEARS) {
      return {
        result: true,
        message: `Добро пожаловать в автошколу "${SCHOOL_NAME}", ${this.name}`,
      };
    }
  };

  this.getTeacherList = () => ["А. С. Иванов", "В. С. Петров", "И. А. Сидоров"];

  this.getTeacher = (id) => {
    const ID = id || Math.floor(Math.random() * this.getTeacherList().length);
    return this.getTeacherList()[ID];
  };

  this.welcome = (name, years) => {
    const SCHOOL_ADDRESS = "Санкт-Петербург, ул. Пушкина, дом 23";

    let userName = name || prompt("Как вас зовут?");

    if (!userName) {
      alert("Вы не указали имя!");
      return name, years;
    }

    let userAge = years || Math.abs(parseFloat(prompt("Укажите ваш возраст")));

    if (!userAge) {
      alert("Вы не указали возраст!");
      return name, years;
    }

    if (this.checkAge(userAge).result) {
      const user = {
        name: userName,
        years: userAge,
      };
      const resultMessage = this.checkAge.bind(user, userAge)();

      alert(resultMessage.message);
    } else if (!this.checkAge(userAge).result) {
      return alert(this.checkAge(userAge).message);
    }

    const TEACHER_NAME = this.getTeacher();

    alert(
      `Ваш преподаватель: ${TEACHER_NAME}\n\nЖдём вас по адресу: ${SCHOOL_ADDRESS}`
    );
    return;
  };

  return {
    welcome: this.welcome,
  };
}

var autoSchool = new School("Парус", 18);
autoSchool.welcome();
autoSchool.welcome("Тест");
autoSchool.welcome("", 15);
autoSchool.welcome("Тест", 16);
autoSchool.welcome("Тест", 18);


```
