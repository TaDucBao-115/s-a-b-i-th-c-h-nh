# s-a-b-i-th-c-h-nh
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(home: AgeChecker());
  }
}

class AgeChecker extends StatefulWidget {
  @override
  _AgeCheckerState createState() => _AgeCheckerState();
}

class _AgeCheckerState extends State<AgeChecker> {
  final nameController = TextEditingController();
  final ageController = TextEditingController();
  String result = '';

  void checkAge() {
    String name = nameController.text;
    int? age = int.tryParse(ageController.text);

    if (name.isEmpty || age == null) {
      setState(() {
        result = "Vui lòng nhập đúng tên và tuổi.";
      });
      return;
    }

    String category = '';
    if (age > 65) {
      category = "Người già";
    } else if (age >= 6) {
      category = "Người lớn";
    } else if (age >= 2) {
      category = "Trẻ em";
    } else {
      category = "Em bé";
    }

    setState(() {
      result = "$name là $category.";
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('bài tập tuần 2')),
      body: Padding(
        padding: const EdgeInsets.all(20.0),
        child: Column(
          children: [
            TextField(
              controller: nameController,
              decoration: InputDecoration(labelText: 'Họ và tên'),
            ),
            TextField(
              controller: ageController,
              decoration: InputDecoration(labelText: 'Tuổi'),
              keyboardType: TextInputType.number,
            ),
            SizedBox(height: 20),
            ElevatedButton(onPressed: checkAge, child: Text('Kiểm tra')),
            SizedBox(height: 20),
            Text(result, style: TextStyle(fontSize: 18)),
          ],
        ),
      ),
    );
  }
}
