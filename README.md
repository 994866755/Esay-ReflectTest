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

}说明一下，最后的return null最好别这么写，返回null不是一个好的做法，我节省时间就暂时这样写
