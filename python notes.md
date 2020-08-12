import datetime
from datetime import datetime
now = datetime.now()
now.year, now.month, now.day
delta = datetime(2011,1,2) - datetime(2001,1,2)
delta.days

from datetime import timedelta
now + 2 * timedelta(days=10)

# 字符串和日期的相互转化
tm.strftime('%I%M%S %p') # 04:01:30 PM
    ''' 格式化字符
    %a星期的简写。如 星期三为Web
    %A星期的全写。如 星期三为Wednesday
    %b月份的简写。如4月份为Apr
    %B月份的全写。如4月份为April
    %c: 日期时间的字符串表示。（如： 04/07/10 10:43:39）
    %d: 日在这个月中的天数（是这个月的第几天）
    %f: 微秒（范围[0,999999]）
    %H: 小时（24小时制，[0, 23]）
    %I: 小时（12小时制，[0, 11]）
    %j: 日在年中的天数 [001,366]（是当年的第几天）
    %m: 月份（[01,12]）
    %M: 分钟（[00,59]）
    %p: AM或者PM
    %S: 秒（范围为[00,61]，为什么不是[00, 59]，参考python手册~_~）
    %U: 周在当年的周数当年的第几周），星期天作为周的第一天
    %w: 今天在这周的天数，范围为[0, 6]，6表示星期天
    %W: 周在当年的周数（是当年的第几周），星期一作为周的第一天
    %x: 日期字符串（如：04/07/10）
    %X: 时间字符串（如：10:43:39）
    %y: 2个数字表示的年份
    %Y: 4个数字表示的年份
    %z: 与utc时间的间隔 （如果是本地时间，返回空字符串）
    %Z: 时区名称（如果是本地时间，返回空字符串）
    %%: %% => %
    '''
datetime.strptime('2011-01-03', '%Y-%m-%d') # str转datetime

datestrs = ['7/6/2011', '8/6/2011']  
[datetime.strptime(x, '%m/%d/%Y') for x in datestrs] # str列表转datetime列表

from dateutil.parser import parse # 直接解析str，转datetime
parse('2011-01-03')
parse('3/1/2011', dayfirst = True)

datestrs = ['2011-07-06 12:00:00', '2011-08-06 00:00:00']
pd.to_datetime(datestrs) # str列表转datetime
idx = pd.to_datetime(datestrs + [None]) # 保留一位NaT not a time

# several immutable classes
'''
datetime.date:表示日期的类,year,month,day;
datetime.time:表示时间的类,hour,minute,second,microsecond;
datetime.datetime:表示日期时间;
datetime.timedelta:表示时间间隔;
datetime.tzinfo:时区相关;
'''
# 其他type转换为datetime type
df.index = pd.to_datetime(df.index)

# class date
## class datetime.date(year, month, day)
day = datetime.date(2019,10,10)
day.max
day.min
day.resolution
day.today()
day.fromtimestamp(timestamp) # 给定时间戳返回date对象
day.weekday() # 定义一个datetime.date类，today.weekday()
day.isoweekday() # 1-7 区别于上面的0-6
day.isoformat() # 按照XXXX-XX-XX的标准格式输出
day.strftime('%y%m%d') # 按给定格式输出 %Y=2019 %y=19
today + day.resolution # 加一天
today - day # return 时间间隔 timedelta()
today < day # False / True

# class time
## class datetime.time(hour=0, minute=0, second=0, microsecond=0, tzinfo=None) 只能比较 不能加减
tm = datetime.time(16,1,30)
tm.replace(hour=14)
tm.isoformat() # 16:01:30

# class datetime
## class datetime.datetime(year, month, day, hour=0, minute=0, second=0, microsecond=0, tzinfo=None)
dtm = datetime.datetime.today()
dtm.date()
dtm.time()
dtm.replace()
dtm.weekday()
dtm.isocalendar() # 迷
dtm.isoformat()
dtm.ctime() # 返回日期的字符串
## 可以加减 可以比较

# class timedelta
## class datetime.timedelta(days=0, seconds=0, microseconds=0, milliseconds=0, minutes=0, hours=0, weeks=0)
