import win32gui
import re

"""
-----获取游戏窗口信息-----
-参数说明：无
-返回值说明：
    info_list: 所有游戏窗口信息列表，由相同类型的信息字典组成。
        字典键值说明：
            platform: 代理平台
            service: 服务器
            name: 账号或备注
            index: 窗口编号
            hwnd: 游戏窗口句柄
-备注：仅适用于36脚本大厅
"""
def get_windows_info():
    windows_list, info_list = [], []
    win32gui.EnumWindows(lambda w, param: param.append(w), windows_list)
    pattern_for_36 = re.compile(r'\[(.*)-(.*)-(.*)]\|(.*)\|(.*)\|(.*)\|(.*)\|(.*)')
    for window in windows_list:
        title = win32gui.GetWindowText(window)
        re_rst = pattern_for_36.search(title)
        if re_rst:
            rst = re_rst.groups()
            info_dict = {'platform': rst[0], 'service': int(rst[1]), 'name': rst[2], 'index': int(rst[3]), 'hwnd': int(rst[5])}
            info_list.append(info_dict)
    return info_list


