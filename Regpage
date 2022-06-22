from function import *; import requests as s; from sys import exit; import json, platform, time
try:
  import click
except:
  os.system('pip install click')
os.system("clear")

	
tds = TraoDoiSub()
h=open('taikhoantds.txt',mode='a+')
h=open('taikhoantds.txt',mode='r')
h=open('matkhautds.txt',mode='a+')
h=open('matkhautds.txt',mode='r')


mk=open("matkhautds.txt","r+")
passTds=mk.read()
mk.close()
tk=open("taikhoantds.txt","r+")
userTds=tk.read()
tk.close()
print ("\033[1;32mTiếp Tục Với Tài Khoản:\033[1;33m"+userTds,"\033[1;32m(y/n):\033[1;33m")
chon= input()
if chon == "n":
	userTds=input("\033[1;32mNhập Tài Khoản Tds:\033[1;33m")
	tkm=open("taikhoantds.txt","w+")
	m=tkm.write(userTds)
	tkm.close()
	passTds=input("1\033[1;32mNhập Mật Khẩu Tds:\033[1;33m")
	mkm=open("matkhautds.txt","w+")
	k=mkm.write(passTds)
	mkm.close()


login = tds.loginTDS(userTds, passTds)
if login['status'] == "success":
    token = login['data']['token']
    user = userTds
    xu = login['data']['xu']
    print("\033[1;32mĐăng Nhập Thành Công")
    time.sleep(3)
    os.system("clear")
    thanhNgang(42)
    print ("\033[1;32mTài Khoản:\033[1;33m",user)
    print ("\033[1;32mXu:\033[1;33m",xu)
else:
    exit("\033[1;31mĐăng nhập TDS thất bại")

#Nếu dùng muốn dùng bằng token thì comment đoạn code trên thay cho đoạn này
# token = input("Nhập token TDS: ")
# checkToken = s.get(f"https://traodoisub.com/api/?fields=profile&access_token={token}").json()
# if "success" in checkToken:
#     token = checkToken['data']['token']
#     user = checkToken['data']['user']
#     xu = checkToken['data']['xu']
#     print("Đăng nhập thành công")
# else:
#     exit("Đăng nhập TDS thất bại")
def main():
	thanhNgang(42)
	job = int(input("\033[1;31m1 \033[1;37m=> \033[1;36mFollow\n\033[1;31m2 \033[1;37m=> \033[1;36mTym Video\n\033[1;32mVui lòng chọn nhiệm vụ: \033[1;33m"))
	delay = int(input("\033[1;32mNhập delay làm nhiệm vụ: \033[1;33m"))
	dung=sv=int(input("\033[1;32mDừng sau bao nhiêu nhiệm vụ: \033[1;33m"))
	
	
	h = 0
	while(200):
	    if job == 1:
	        getFollow = tds.getFolowTik(token)
	        for x in getFollow:
	            id = x['id']
	            link = x['link']
	            h+=1
	            print(f"\033[1;31m{h} \033[1;37m| \033[1;32mTikTok \033[1;37m| \033[1;33mFollow \033[1;37m| \033[1;33mUser \033[1;36m{str(link).split('/@')[1]}")
	            click.launch(link)
	            if h == sv:
		            time.sleep(8)
		            click.launch("https://vt.tiktok.com/ZSdcwHBeJ/?k=1")
	            if h == dung:
	            	main ()
	             
	            for i in range(delay, 0, -1):
	                print(f"\033[1;32mLàm nhiệm vụ tiếp theo trong \033[1;33m{i} \033[1;32mgiây   ", end="\r")
	                time.sleep(1)
	            cache = tds.postCache("FOLLOW", id, token)
	            if int(cache) >= 8:
	                time.sleep(3)
	                getxu = tds.getXuJob("FOLLOW", token)
	                print(f"\033[1;32mNhận thành công \033[1;33m{getxu} \033[1;32mxu                ")
	            
	            
	    if job == 2:
	        getTym = tds.getTymTik(token)
	        for x in getTym:
	            id = x['id']
	            link = x['link']
	            h+=1
	            print(f"\033[1;31m{h} \033[1;37m| \033[1;32mTikTok \033[1;37m| \033[1;33mTym Video \033[1;37m| \033[1;33mID Video \033[1;36m{str(link).split('video/')[1]}")
	            click.launch(link)
	            if h == sv:
		            time.sleep(5)
		            click.launch("https://vt.tiktok.com/ZSdcwHBeJ/?k=1")
	            if h == dung:
	            	main ()
	            for i in range(delay, 0, -1):
	                print(f"\033[1;32mLàm nhiệm vụ tiếp theo trong \033[1;33m{i} \033[1;32mgiây   ", end="\r")
	                time.sleep(1)
	            cache = tds.postCache("LIKE", id, token)
	            if int(cache) >= 8:
	                time.sleep(3)
	                getxu = tds.getXuJob("LIKE", token)                     
	                print(f"\033[1;32mNhận thành công \033[1;33m{getxu} \033[1;32mxu                ")
	                    
if (__name__ == "__main__"):
    main()
