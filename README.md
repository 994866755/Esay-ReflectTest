# Esay-ReflectTest
第一次使用泛型和反射，自己写了个简单的程序
写一个类简单地去完成反射的功能

public class Reflect<E> {

    private E e;
    private Class<?> c;
    private Method method;

    public Reflect(E e){
        this.e = e;
        c = e.getClass();
    }

    public void rSet(String str){
        try {
            method = c.getDeclaredMethod("setUsername",new Class[]{String.class});
            method.invoke(e,str);
        } catch (NoSuchMethodException e1) {
            e1.printStackTrace();
        } catch (InvocationTargetException e1) {
            e1.printStackTrace();
        } catch (IllegalAccessException e1) {
            e1.printStackTrace();
        }
    }

    public String rGet(){
        try {
            method = c.getDeclaredMethod("getUsername",null);
            return (String) method.invoke(e,null);
        } catch (NoSuchMethodException e1) {
            e1.printStackTrace();
        } catch (InvocationTargetException e1) {
            e1.printStackTrace();
        } catch (IllegalAccessException e1) {
            e1.printStackTrace();
        }
        return null;
    }

}

说明一下，最后的return null最好别这么写，返回null不是一个好的做法，我节省时间就暂时这样写

这样子就能完成一个简单的反射了，通过传进来的对象，可以动态地拿到它的类名和方法。

关于一个简单的反射功能就这样实现了，当然还有不同的获取类名和方法的做法，这里就不说明，API也毕竟容易能看懂，至于什么时候会用到反射和怎样最合理地去使用反射效果最好，以后总结好了再发新的文章说明吧。这里我也是刚用github，写个简单的项目测试一下。
