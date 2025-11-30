<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>مدرسة عين الباشا الثانوية - قابل للتعديل</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; padding: 0; background-color: #ffffff; color: #333; }
        header { background-color: #007bff; color: white; text-align: center; padding: 30px; }
        nav { background-color: #e3f2fd; padding: 15px; text-align: center; }
        nav a { color: #007bff; margin: 0 20px; text-decoration: none; font-weight: bold; }
        section { padding: 20px; margin: 20px; background-color: #ffffff; border: 1px solid #007bff; border-radius: 8px; position: relative; }
        footer { text-align: center; padding: 15px; background-color: #007bff; color: white; }
        .edit-btn { position: absolute; top: 10px; right: 10px; background-color: #28a745; color: white; border: none; padding: 5px 10px; cursor: pointer; }
        .edit-form { display: none; margin-top: 10px; }
        textarea { width: 100%; height: 100px; }
        button { padding: 8px; background-color: #007bff; color: white; border: none; cursor: pointer; margin: 5px; }
    </style>
</head>
<body>
    <header>
        <h1>مدرسة عين الباشا الثانوية</h1>
        <p id="header-text">نحن نعمل على بناء مستقبل أفضل لطلابنا</p>
        <button class="edit-btn" onclick="editSection('header-text')">تعديل</button>
        <div class="edit-form" id="header-form">
            <textarea id="header-input"></textarea><br>
            <button onclick="saveSection('header-text', 'header-input')">حفظ</button>
            <button onclick="cancelEdit('header-form')">إلغاء</button>
        </div>
    </header>
    
    <nav>
        <a href="#about">عن المدرسة</a>
        <a href="#students">الطلاب</a>
        <a href="#news">الأخبار</a>
        <a href="#contact">اتصل بنا</a>
    </nav>
    
    <section id="about">
        <h2>عن المدرسة</h2>
        <p id="about-text">مدرسة عين الباشا الثانوية هي مؤسسة تعليمية رائدة تقدم تعليماً شاملاً للطلاب في المرحلة الثانوية. نحن نركز على التميز الأكاديمي والنشاطات الرياضية والثقافية.</p>
        <button class="edit-btn" onclick="editSection('about-text')">تعديل</button>
        <div class="edit-form" id="about-form">
            <textarea id="about-input"></textarea><br>
            <button onclick="saveSection('about-text', 'about-input')">حفظ</button>
            <button onclick="cancelEdit('about-form')">إلغاء</button>
        </div>
    </section>
    
    <section id="students">
        <h2>الطلاب</h2>
        <p id="students-text">لدينا أكثر من 500 طالب مسجل. يمكنك العثور على معلومات حول البرامج التعليمية والأنشطة هنا.</p>
        <button class="edit-btn" onclick="editSection('students-text')">تعديل</button>
        <div class="edit-form" id="students-form">
            <textarea id="students-input"></textarea><br>
            <button onclick="saveSection('students-text', 'students-input')">حفظ</button>
            <button onclick="cancelEdit('students-form')">إلغاء</button>
        </div>
    </section>
    
    <section id="news">
        <h2>الأخبار</h2>
        <p id="news-text">أحدث الأخبار: افتتاح مكتبة جديدة في المدرسة. تابعونا للمزيد من التحديثات.</p>
        <button class="edit-btn" onclick="editSection('news-text')">تعديل</button>
        <div class="edit-form" id="news-form">
            <textarea id="news-input"></textarea><br>
            <button onclick="saveSection('news-text', 'news-input')">حفظ</button>
            <button onclick="cancelEdit('news-form')">إلغاء</button>
        </div>
    </section>
    
    <section id="contact">
        <h2>اتصل بنا</h2>
        <p id="contact-text">العنوان: عين الباشا، [المدينة/الدولة]<br>الهاتف: [رقم الهاتف]<br>البريد الإلكتروني: info@ainbashasecondary.edu</p>
        <button class="edit-btn" onclick="editSection('contact-text')">تعديل</button>
        <div class="edit-form" id="contact-form">
            <textarea id="contact-input"></textarea><br>
            <button onclick="saveSection('contact-text', 'contact-input')">حفظ</button>
            <button onclick="cancelEdit('contact-form')">إلغاء</button>
        </div>
    </section>
    
    <footer>
        <p>&copy; 2023 مدرسة عين الباشا الثانوية. جميع الحقوق محفوظة.</p>
    </footer>
    
    <script>
        // تحميل النصوص المحفوظة عند تحميل الصفحة
        window.onload = function() {
            ['header', 'about', 'students', 'news', 'contact'].forEach(id => {
                const saved = localStorage.getItem(id + '-text');
                if (saved) document.getElementById(id + '-text').innerHTML = saved;
            });
        };
        
        // فتح نموذج التعديل
        function editSection(textId) {
            const formId = textId.replace('-text', '-form');
            document.getElementById(formId).style.display = 'block';
            document.getElementById(textId.replace('-text', '-input')).value = document.getElementById(textId).innerHTML.replace(/<br>/g, '\n');
        }
        
        // حفظ التعديل
        function saveSection(textId, inputId) {
            const newText = document.getElementById(inputId).value.replace(/\n/g, '<br>');
            document.getElementById(textId).innerHTML = newText;
            localStorage.setItem(textId, newText);
            cancelEdit(textId.replace('-text', '-form'));
        }
        
        // إلغاء التعديل
        function cancelEdit(formId) {
            document.getElementById(formId).style.display = 'none';
        }
    </script>
</body>
</html>
