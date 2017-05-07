#   BenefitEventDomain

### 初审用构造函数
```java
/**
	 * 初审用构造函数
	 * Constructors
	 * @param aaz170 事件ID
	 * @param aaa121 业务类型编码
	 * @param aab001 单位ID
	 * @param aac001 人员ID
	 * @param aae140 险种类型
	 * @param aaz257 享受定期待遇人员ID
	 * @param aae016 复核标志
	 * @param yab139 参保所属机构
	 * @param aaz002 业务日志ID
	 * @param aae013 备注
	 * @param aaa027 统筹区
	 * @param user 经办信息：传入getUserInfo()
	 */
	public BenefitEventDomain(String aaz170, String aaa121, String aab001, String aac001, String aae140, String aaz257, String aae016, String yab139, String aaz002, String aae013, String aaa027, IUser user)
```

### 初审保存方法

```java
/**
	 * 保存待遇事件
	 * @author tianqi
	 * @see 
	 * @throws Exception
	 * @datetime 2016年8月1日 下午3:46:13
	 * @version 1.0
	 */
	public void toSave() throws Exception
```

### 复核时用构造函数
```java
/**
	 * 复核用构造函数
	 * Constructors
	 */
	public BenefitEventDomain()
```

### 更新为复核通过
```java
/**
	 * 更新为复核通过
	 * @author tianqi
	 * @see 
	 * @return
	 * @throws Exception
	 * @datetime 2016年8月1日 下午3:57:19
	 * @version 1.0
	 */
	public int adopted(String aaz002, IUser user) throws Exception
```

### 更新为复核不通过
```java
/**
	 * 更新为复核不通过
	 * @author tianqi
	 * @see 
	 * @return
	 * @throws Exception
	 * @datetime 2016年8月1日 下午3:57:19
	 * @version 1.0
	 */
	public int deny(String aaz002, IUser user) throws Exception
```

### 更新为未复核
```java
/**
	 * 更新为未复核
	 * @author tianqi
	 * @see 
	 * @return
	 * @throws Exception
	 * @datetime 2016年8月1日 下午3:57:19
	 * @version 1.0
	 */
	public int unintercept(String aaz002, IUser user) throws Exception
```

