# آموزش دستورات پایه گیت (Git)

## شروع کار با گیت

### اضافه کردن گیت به پروژه
برای شروع کار با گیت در یک پروژه جدید، باید مخزن گیت را در آن پوشه ایجاد کنیم:

```
> git init
Initialized empty Git repository in .git/
```

این دستور، یک پوشه مخفی به نام `.git` ایجاد می‌کند که تمام اطلاعات مربوط به تغییرات و تاریخچه پروژه در آن ذخیره می‌شود.

## بررسی وضعیت فایل‌ها

برای مشاهده وضعیت فعلی فایل‌ها (تغییرات، فایل‌های ردیابی نشده و غیره) از دستور زیر استفاده می‌کنیم:

```
> git status
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .idea/
        git.md
        test1.py
nothing added to commit but untracked files present (use "git add" to track) 
```

این دستور نشان می‌دهد که در شاخه `master` هستیم، هنوز هیچ کامیتی انجام نداده‌ایم و فایل‌های `.idea/`، `git.md` و `test1.py` در وضعیت ردیابی نشده (untracked) قرار دارند.

## مدیریت فایل‌ها در Staging Area

### انتقال فایل از Working Directory به Staging Area
برای اضافه کردن یک فایل خاص به Staging Area:

```
> git add test1.py
```

برای اضافه کردن همه فایل‌ها به Staging Area:

```
> git add .
```

### برگرداندن فایل از Staging Area به Working Directory
اگر بخواهیم فایلی را از Staging Area خارج کنیم:

```
> git rm --cached test1.py
rm 'test1.py'
```

توجه: این دستور فایل را از دیسک حذف نمی‌کند، بلکه فقط از لیست فایل‌های آماده برای کامیت خارج می‌کند.

## ثبت تغییرات در مخزن (Repository)

برای ثبت تغییرات در مخزن گیت (کامیت کردن):

```
> git commit -m 'create new file test2.py'
[master 24afd1c] create new file test2.py
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test2.py
```

پیام کامیت باید توضیح مختصر و مفیدی از تغییرات ایجاد شده باشد.

## چرخه کاری گیت

1. **Working Directory**: محیط کاری شما که فایل‌ها را در آن ویرایش می‌کنید
2. **Staging Area (Index)**: فایل‌هایی که برای کامیت بعدی آماده شده‌اند
3. **Repository**: مخزن اصلی که تاریخچه همه تغییرات را نگهداری می‌کند

دستورات اصلی برای حرکت بین این مراحل:
- `git add`: Working → Staging
- `git rm --cached`: Staging → Working
- `git commit`: Staging → Repository

## دستورات پیشرفته git log برای بررسی تاریخچه تغییرات

### نمایش کامل تغییرات
برای دیدن جزئیات کامل تمام کامیت‌ها:

```bash
> git log
```
این دستور اطلاعات کامل شامل:
- هش کامیت
- نام نویسنده
- ایمیل
- تاریخ
- پیام کامیت

### نمایش خلاصه تغییرات
برای نمایش خلاصه کامیت‌ها در یک خط:

```bash
> git log --oneline
```
مفید برای مشاهده سریع تاریخچه تغییرات

### نمایش آماری تغییرات
برای دیدن تعداد تغییرات در هر کامیت:

```bash
> git log --stat
```
نشان می‌دهد چه فایل‌هایی تغییر کرده و تعداد خطوط اضافه/حذف شده

### نمایش گرافیکی تغییرات
برای نمایش گرافیکی شاخه‌ها و کامیت‌ها:

```bash
> git log --graph
```
```bash
> git log --graph --oneline  # نمایش خلاصه گرافیکی
```

### فیلتر کردن کامیت‌ها بر اساس زمان
جستجوی کامیت‌ها پس از یک تاریخ خاص:

```bash
> git log --after="25-02-3"
```

### فیلتر کردن کامیت‌ها بر اساس نویسنده
نمایش کامیت‌های یک نویسنده خاص:

```bash
> git log --author="نام نویسنده"
```

## نکات مهم
- هر کامیت یک هش منحصر به فرد دارد
- می‌توانید با استفاده از این دستورات، تاریخچه تغییرات را به دقت بررسی کنید
- فیلترهای مختلف امکان جستجوی دقیق در تاریخچه را فراهم می‌کنند


### کامیت مستقیم با `-a`

برای اضافه کردن و کامیت کردن همزمان فایل‌های تغییر یافته (فقط برای فایل‌هایی که قبلاً تحت کنترل گیت هستند):

```bash
> git commit -am "update test1"
[master aa3e98e] update test1
 1 file changed, 3 insertions(+), 1 deletion(-)
```

این دستور ترکیبی از `git add` (برای فایل‌های تغییر یافته، نه فایل‌های جدید) و `git commit` است.

پس از اجرای دستور، وضعیت مخزن به این صورت خواهد بود:

```bash
> git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working tree clean
```

### مشاهده جزئیات یک کامیت

برای مشاهده تغییرات دقیق در یک کامیت مشخص:

```bash
> git show aa3e98e
commit aa3e98e45306244b804092315e2e6b1228db31ab (HEAD -> master)
Author: hosseindehghandehnavi <dehghandehnavihossein@gmail.com>
Date:   Sat Mar 8 10:47:23 2025 +0330
    update test1
diff --git a/test1.py b/test1.py
index c70ced9..0cdb229 100644
--- a/test1.py
+++ b/test1.py
@@ -1,2 +1,4 @@
 x = 21
-print('x =',x)
\ No newline at end of file
+print('x =',x)
+
+print("hello world")
\ No newline at end of file
```

همچنین می‌توان تغییرات یک فایل خاص در کامیت را مشاهده کرد:

```bash
> git show aa3e98e test2.py
```

### تعریف نام مستعار (Alias) برای دستورات

برای ساده‌تر کردن دستورات پیچیده و تکراری، می‌توان از نام مستعار استفاده کرد:

```bash
> git log --oneline
aa3e98e (HEAD -> master) update test1
2fee4a7 (origin/master) update
c5f55a1 add git log
a143203 Updating and improving git.md with AI
bcd9120 transfer to repo
24afd1c create new file test2.py
b778f48 create new file test2.py
```

تعریف نام مستعار برای پروژه فعلی (محلی):

```bash
> git config --local alias.lgo "log --oneline"
```

اکنون می‌توان از دستور کوتاه‌تر استفاده کرد:

```bash
> git lgo
aa3e98e (HEAD -> master) update test1
2fee4a7 (origin/master) update
c5f55a1 add git log
a143203 Updating and improving git.md with AI
bcd9120 transfer to repo
24afd1c create new file test2.py
b778f48 create new file test2.py
```

**نکته مهم**: نام مستعار تعریف شده با `--local` فقط در پروژه جاری قابل استفاده است. برای استفاده در تمام پروژه‌ها، باید از `--global` استفاده کنید:

```bash
> git config --global alias.lgo "log --oneline"
```

### مزایای استفاده از نام مستعار

1. کاهش تایپ برای دستورات پیچیده و طولانی
2. ایجاد میانبر برای ترکیب‌های پرکاربرد دستورات
3. سفارشی‌سازی واسط کاربری گیت مطابق با نیازهای شخصی

# کار با شاخه‌ها (Branch) در گیت

## مفهوم برنچ (شاخه)
برنچ‌ها یا شاخه‌ها امکان کار روی نسخه‌های مختلف از کد را به صورت همزمان فراهم می‌کنند. هر برنچ یک مسیر مستقل از توسعه است.

### دلایل استفاده از برنچ
- توسعه ویژگی‌های جدید بدون تأثیر بر کد اصلی
- اصلاح باگ‌ها به صورت جداگانه
- تست کدها و افزونه‌ها
- امکان همکاری چندین توسعه‌دهنده بر روی یک پروژه
- جداسازی نسخه‌های پایدار و توسعه‌ای

## دستورات اصلی مدیریت برنچ

### مشاهده برنچ‌های موجود
```bash
> git branch
* master
```
علامت `*` نشان می‌دهد که در حال حاضر روی کدام برنچ هستیم.

### ایجاد برنچ جدید
```bash
> git branch Test
```
این دستور یک برنچ جدید به نام `Test` می‌سازد اما به آن سوئیچ نمی‌کند.

### سوئیچ کردن بین برنچ‌ها
```bash
> git switch Test
Switched to branch 'Test'
```

### ایجاد و سوئیچ همزمان
```bash
> git switch -c Test2
Switched to a new branch 'Test2'
```
این دستور یک برنچ جدید می‌سازد و بلافاصله به آن سوئیچ می‌کند.

### حذف برنچ
```bash
> git branch -d Test2
```
**نکته مهم**: نمی‌توانید برنچی که در حال حاضر روی آن هستید را حذف کنید:
```bash
> git branch -d Test2
error: Cannot delete branch 'Test2' checked out at '...'
```
ابتدا باید به برنچ دیگری سوئیچ کنید، سپس برنچ مورد نظر را حذف کنید:
```bash
> git switch master
> git branch -d Test2
Deleted branch Test2 (was e77182e).
```

### تغییر نام برنچ
برای تغییر نام یک برنچ، ابتدا باید روی آن برنچ باشید:
```bash
> git switch Test
Switched to branch 'Test'
> git branch -m TestPrint
> git branch
* TestPrint
  master
```

## ادغام (Merge) برنچ‌ها

ادغام برنچ‌ها به دو روش انجام می‌شود:

### 1. ادغام Fast-Forward
زمانی که هیچ تغییری در برنچ مقصد (معمولاً `master`) ایجاد نشده باشد:

```bash
> git switch master
Switched to branch 'master'
> git merge TestPrint
Updating 56bcbec..e77182e
Fast-forward
 test1.py | 4 +++-
 1 file changed, 3 insertions(+), 1 deletion(-)
```

در این حالت، گیت فقط اشاره‌گر برنچ مقصد را به آخرین کامیت برنچ منبع منتقل می‌کند.

### 2. ادغام Non-Fast-Forward
زمانی که هر دو برنچ تغییراتی داشته باشند، دو حالت پیش می‌آید:

#### الف) ادغام بدون تداخل (No Conflict)
اگر تغییرات در فایل‌های متفاوت یا خطوط مختلف از یک فایل باشند:

```bash
> git switch master
> git merge feature-branch
Merge made by the 'recursive' strategy.
 file1.txt | 2 ++
 1 file changed, 2 insertions(+)
```

در این حالت، گیت یک کامیت جدید ایجاد می‌کند که تغییرات هر دو برنچ را شامل می‌شود.

#### ب) ادغام با تداخل (Conflict)
اگر تغییرات در خطوط یکسان از یک فایل باشند:

```bash
> git merge feature-branch
Auto-merging file1.txt
CONFLICT (content): Merge conflict in file1.txt
Automatic merge failed; fix conflicts and then commit the result.
```

در این حالت باید تداخل را به صورت دستی حل کنید:

1. فایل‌های دارای تداخل را باز کنید
2. بخش‌های مشخص شده با `<<<<<<< HEAD`, `=======`, و `>>>>>>> feature-branch` را ویرایش کنید
3. تغییرات را اضافه کرده و کامیت کنید:
   ```bash
   > git add file1.txt
   > git commit -m "Resolve merge conflict"
   ```

## توصیه‌هایی برای جلوگیری از تداخل
1. هر برنچ را برای یک هدف مشخص و محدود ایجاد کنید
2. به طور منظم برنچ اصلی را با برنچ خود ادغام کنید
3. تغییرات کوچک و مکرر را کامیت کنید
4. ارتباط مداوم با سایر توسعه‌دهندگان داشته باشید
5. از ابزارهای مدیریت برنچ مانند GitFlow استفاده کنید

## استاندارد نوشتن پیام کامیت
برای رعایت استاندارد در نوشتن پیام‌های کامیت، می‌توانید از این منابع استفاده کنید:
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [Commit Message Guidelines](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716)

**فرمت پیشنهادی**:
```
<نوع>: <توضیح مختصر>

<توضیحات جزئی>
```

**انواع متداول**:
- `feat`: ویژگی جدید
- `fix`: رفع باگ
- `docs`: تغییر در مستندات
- `style`: تغییرات ظاهری (فرمت کد)
- `refactor`: بازنویسی کد بدون تغییر در عملکرد
- `test`: اضافه کردن یا اصلاح تست‌ها
- `chore`: تغییرات متفرقه