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