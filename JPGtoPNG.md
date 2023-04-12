import os
from PIL import Image
img_dir = './JPG' # duong dan toi thu muc chua file anh

img_new = './PNG'
if os.path.exists(img_new): #kiem tra xem file co trong thu muc khong
    print('File exists')
else:
    print('File does not exist')

# duyệt qua tất cả các file trong thư mục và đổi đuôi
for filename in os.listdir(img_dir):
    if filename.endswith(".jpg"):
        # tạo đường dẫn đầy đủ tới file ảnh
        img_path = os.path.join(img_dir, filename)
        # đọc file ảnh vào bằng Pillow
        with Image.open(img_path) as im:
            # tạo đường dẫn đầy đủ tới file mới
            new_path = os.path.join(img_new, os.path.splitext(filename)[0]+'.png')
            # lưu file ảnh mới với định dạng .png
            im.save(new_path, "PNG")
            print(f"Đổi đuôi {filename} thành {os.path.basename(new_path)}")
