
# Flutter Atomic Design

Este repositório demonstra como aplicar a metodologia de Atomic Design no desenvolvimento de interfaces de usuário com Flutter. O Atomic Design, popularizado por Brad Frost, ajuda a criar sistemas de design escaláveis e reutilizáveis ao dividir a UI em componentes menores.

<img src="https://bradfrost.com/wp-content/uploads/2013/06/atomic-design.png" alt="Atomic Design" height="400">

## 📌 O que é Atomic Design?

**Atomic Design** é uma abordagem que organiza a construção de interfaces de usuário em cinco níveis:

1. **Átomos**: Elementos básicos como botões, textos, ícones.
2. **Moléculas**: Combinações de átomos, como um campo de texto com um botão.
3. **Organismos**: Grupos de moléculas que formam seções da UI, como um cabeçalho.
4. **Templates**: Estruturas de layout que organizam organismos.
5. **Páginas**: Templates preenchidos com conteúdo específico, representando a versão final do design.

## 📱 Aplicando ao Flutter

### 🧩 Átomos

No Flutter, átomos são widgets simples, como `Text`, `Button`, `Icon`, etc.

#### Exemplo:

```dart
// lib/atoms/my_text.dart
import 'package:flutter/material.dart';

class MyText extends StatelessWidget {
  final String text;
  
  const MyText({required this.text, super.key});

  @override
  Widget build(BuildContext context) {
    return Text(
      text,
      style: TextStyle(fontSize: 24, color: Colors.blue),
    );
  }
}
```

### 🔗 Moléculas

Moléculas combinam átomos. Por exemplo, um campo de entrada com um botão de envio.

#### Exemplo:

```dart
// lib/molecules/my_input_field.dart
import 'package:flutter/material.dart';
import '../atoms/my_text.dart';

class MyInputField extends StatelessWidget {
  final String label;
  final String buttonText;

  const MyInputField({required this.label, required this.buttonText, super.key});

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        TextField(decoration: InputDecoration(labelText: label)),
        ElevatedButton(
          onPressed: () {},
          child: MyText(text: buttonText),
        ),
      ],
    );
  }
}
```

### 🏗️ Organismos

Organismos são componentes mais complexos, como um formulário completo.

#### Exemplo:

```dart
// lib/organisms/login_form.dart
import 'package:flutter/material.dart';
import '../molecules/my_input_field.dart';

class LoginForm extends StatelessWidget {
  const LoginForm({super.key});

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        const Text('Login Form', style: TextStyle(fontSize: 32)),
        const MyInputField(label: 'Username', buttonText: 'Submit'),
        const MyInputField(label: 'Password', buttonText: 'Submit'),
      ],
    );
  }
}
```

### 📑 Templates

Templates organizam organismos em layouts de página.

#### Exemplo:

```dart
// lib/templates/profile_template.dart
import 'package:flutter/material.dart';
import '../organisms/login_form.dart';

class ProfileTemplate extends StatelessWidget {
  const ProfileTemplate({super.key});

  @override
  Widget build(BuildContext context) {
    return Column(
      children: const [
        Text('Profile Header', style: TextStyle(fontSize: 32)),
        LoginForm(),
        // Other profile details
      ],
    );
  }
}
```

### 🌐 Páginas

Páginas são templates com conteúdo específico.

#### Exemplo:

```dart
// lib/pages/user_profile_page.dart
import 'package:flutter/material.dart';
import '../templates/profile_template.dart';

class UserProfilePage extends StatelessWidget {
  const UserProfilePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('User Profile')),
      body: const Center(
        child: ProfileTemplate(),
      ),
    );
  }
}
```

## 🚀 Benefícios do Atomic Design com Flutter

- **Reutilização de componentes**: Crie widgets reutilizáveis, reduzindo a duplicação de código.
- **Manutenção facilitada**: Alterações em um componente se propagam facilmente.
- **Consistência**: Garantia de uma UI coesa e uniforme.

## 📚 Recursos adicionais

- [Documentação do Flutter](https://flutter.dev/docs)
- [Atomic Design por Brad Frost](http://bradfrost.com/blog/post/atomic-web-design/)
