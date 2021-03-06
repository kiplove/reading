# StringBuilder
 * StringBuilder继承AbstractStringBuilder并实现了Serializable和CharSequence接口
 * AbstractStringBuilder类有两个成员变量：
 * byte[] value;  StringBuilder的存放值，区别于String类型使用final修饰，所以StringBuilder是可变的
 * int count;     数组的大小
 * CharSequence接口是String，StringBuilder和StringBuffer共有的接口，提供序列化字符基本的操作，包括length，charAt，codePoints，toString

 
## 源码
    /**
     * 序列化
     */
    static final long serialVersionUID = 4383685877147921099L;

	
    /**
	 * 接下来是4个构造函数，一个无参，一个以容量为参数，两个以字符类型为参数
     * 
     * 调用AbstractStringBuilder接口，默认初始化value容量为16
     */
    @HotSpotIntrinsicCandidate
    public StringBuilder() {
        super(16);
    }

    /**
	 *	以capacity为value初始化大小
     */
    @HotSpotIntrinsicCandidate
    public StringBuilder(int capacity) {
        super(capacity);
    }

    /**
	 * 用string类型初始化
     */
    @HotSpotIntrinsicCandidate
    public StringBuilder(String str) {
        super(str.length() + 16);
        append(str);
    }

    /**
	 * 用CharSequence类型初始化
     */
    public StringBuilder(CharSequence seq) {
        this(seq.length() + 16);
        append(seq);
    }

	
	/**
	 * 接下来是13个append方法，前四个是以不同字符参数作为拼接对象
	 *
	 */
    @Override
    public StringBuilder append(Object obj) {
        return append(String.valueOf(obj));
    }

    @Override
    @HotSpotIntrinsicCandidate
    public StringBuilder append(String str) {
        super.append(str);
        return this;
    }


    public StringBuilder append(StringBuffer sb) {
        super.append(sb);
        return this;
    }

    @Override
    public StringBuilder append(CharSequence s) {
        super.append(s);
        return this;
    }

    /**
     *  这三个给出是数组或者有范围的数组，所以可以会有超出范围的异常出现
     */
    @Override
    public StringBuilder append(CharSequence s, int start, int end) {
        super.append(s, start, end);
        return this;
    }

    @Override
    public StringBuilder append(char[] str) {
        super.append(str);
        return this;
    }

    @Override
    public StringBuilder append(char[] str, int offset, int len) {
        super.append(str, offset, len);
        return this;
    }

	/**
	 * 下面六种，将不同的基本类型作为拼接对象
	 */
    @Override
    public StringBuilder append(boolean b) {
        super.append(b);
        return this;
    }

    @Override
    @HotSpotIntrinsicCandidate
    public StringBuilder append(char c) {
        super.append(c);
        return this;
    }

    @Override
    @HotSpotIntrinsicCandidate
    public StringBuilder append(int i) {
        super.append(i);
        return this;
    }

    @Override
    public StringBuilder append(long lng) {
        super.append(lng);
        return this;
    }

    @Override
    public StringBuilder append(float f) {
        super.append(f);
        return this;
    }

    @Override
    public StringBuilder append(double d) {
        super.append(d);
        return this;
    }
	

    /**
     * 将Unicode编码所代表的字符作为拼接对象
     */
    @Override
    public StringBuilder appendCodePoint(int codePoint) {
        super.appendCodePoint(codePoint);
        return this;
    }

    /**
     * 删除一段字符按位置，注意范围
     */
    @Override
    public StringBuilder delete(int start, int end) {
        super.delete(start, end);
        return this;
    }

    /**
     * 删除一个字符按位置
     */
    @Override
    public StringBuilder deleteCharAt(int index) {
        super.deleteCharAt(index);
        return this;
    }

    /**
     * 用str替换一段字符String
     */
    @Override
    public StringBuilder replace(int start, int end, String str) {
        super.replace(start, end, str);
        return this;
    }

    /**
     * 插入一段字符char[]
     */
    @Override
    public StringBuilder insert(int index, char[] str, int offset,
                                int len)
    {
        super.insert(index, str, offset, len);
        return this;
    }

    /**
     * 插入一段字符Object
     */
    @Override
    public StringBuilder insert(int offset, Object obj) {
            super.insert(offset, obj);
            return this;
    }

    /**
     * 用str插入一段字符String
     */
    @Override
    public StringBuilder insert(int offset, String str) {
        super.insert(offset, str);
        return this;
    }

    /**
     * 插入一段字符char[]
     */
    @Override
    public StringBuilder insert(int offset, char[] str) {
        super.insert(offset, str);
        return this;
    }

    /**
     * 插入一段字符
     */
    @Override
    public StringBuilder insert(int dstOffset, CharSequence s) {
            super.insert(dstOffset, s);
            return this;
    }

    /**
     * 插入一段字符
     */
    @Override
    public StringBuilder insert(int dstOffset, CharSequence s,
                                int start, int end)
    {
        super.insert(dstOffset, s, start, end);
        return this;
    }

    /**
     * 插入一个基本类型
     */
    @Override
    public StringBuilder insert(int offset, boolean b) {
        super.insert(offset, b);
        return this;
    }

    /**
     * @throws IndexOutOfBoundsException {@inheritDoc}
     */
    @Override
    public StringBuilder insert(int offset, char c) {
        super.insert(offset, c);
        return this;
    }

    /**
     * @throws StringIndexOutOfBoundsException {@inheritDoc}
     */
    @Override
    public StringBuilder insert(int offset, int i) {
        super.insert(offset, i);
        return this;
    }

    /**
     * @throws StringIndexOutOfBoundsException {@inheritDoc}
     */
    @Override
    public StringBuilder insert(int offset, long l) {
        super.insert(offset, l);
        return this;
    }

    /**
     * @throws StringIndexOutOfBoundsException {@inheritDoc}
     */
    @Override
    public StringBuilder insert(int offset, float f) {
        super.insert(offset, f);
        return this;
    }

    /**
     * @throws StringIndexOutOfBoundsException {@inheritDoc}
     */
    @Override
    public StringBuilder insert(int offset, double d) {
        super.insert(offset, d);
        return this;
    }

    @Override
    public int indexOf(String str) {
        return super.indexOf(str);
    }

    @Override
    public int indexOf(String str, int fromIndex) {
        return super.indexOf(str, fromIndex);
    }

    @Override
    public int lastIndexOf(String str) {
        return super.lastIndexOf(str);
    }

    @Override
    public int lastIndexOf(String str, int fromIndex) {
        return super.lastIndexOf(str, fromIndex);
    }

    @Override
    public StringBuilder reverse() {
        super.reverse();
        return this;
    }

    @Override
    @HotSpotIntrinsicCandidate
    public String toString() {
        // Create a copy, don't share the array
        return isLatin1() ? StringLatin1.newString(value, 0, count)
                          : StringUTF16.newString(value, 0, count);
    }

	/**
	 * 将stringbuilder写到ObjectOutputStream中
	 */
    private void writeObject(java.io.ObjectOutputStream s)
        throws java.io.IOException {
        s.defaultWriteObject();
        s.writeInt(count);
        char[] val = new char[capacity()];
        if (isLatin1()) {
            StringLatin1.getChars(value, 0, count, val, 0);
        } else {
            StringUTF16.getChars(value, 0, count, val, 0);
        }
        s.writeObject(val);
    }

    /**
     * 将ObjectInputStream读取到val中
     */
    private void readObject(java.io.ObjectInputStream s)
        throws java.io.IOException, ClassNotFoundException {
        s.defaultReadObject();
        count = s.readInt();
        char[] val = (char[]) s.readObject();
        initBytes(val, 0, val.length);
    }

