import datetime
import os

# 打卡记录文件
log_file = 'daily_check_in.log'

def check_in():
    # 获取当前日期和时间
    now = datetime.datetime.now()
    date_str = now.strftime('%Y-%m-%d')
    time_str = now.strftime('%H:%M:%S')

    # 打开文件并写入打卡记录
    with open(log_file, 'a') as file:
        file.write(f'{date_str} {time_str}\n')

    print(f'打卡成功！当前时间：{time_str}')

def view_log():
    # 检查文件是否存在
    if not os.path.exists(log_file):
        print('没有找到打卡记录文件。')
        return

    # 读取并显示文件内容
    with open(log_file, 'r') as file:
        content = file.read()
        print('打卡记录：')
        print(content)

def main():
    while True:
        print('\n1. 打卡')
        print('2. 查看打卡记录')
        print('3. 退出')
        choice = input('请选择操作：')

        if choice == '1':
            check_in()
        elif choice == '2':
            view_log()
        elif choice == '3':
            break
        else:
            print('无效的选择，请重试。')

if __name__ == '__main__':
    main()
