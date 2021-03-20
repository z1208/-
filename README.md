# -package test;
import java.util.Scanner;
abstract class Shape{
	public abstract double calcuPerimeter();
	public abstract double calcuArea();
	public abstract void getType();
}
/**
 * 三角形
 * @author dell
 *
 */
class Triangle extends Shape{
	double a;
	double b;
	double c;
	public Triangle(double a, double b, double c) {
		this.a = a;
		this.b = b;
		this.c = c;
	}
	public double calcuPerimeter() {
		double perimeter = a + b + c;
		return perimeter;
	}
	public double calcuArea() {
		double s = (a + b + c) / 2;
		double area = Math.pow(s*((s - a)*(s - b)*(s - c)), 0.5);
		return area;
	}
	public void getType() {
		System.out.println("我是一个三角形！");
	}
}
/**
 * 矩形
 * @author dell
 *
 */
class Rect extends Shape{
	double width;
	double height;
	Rect(double width,double height){
		this.width=width;
		this.height=height;
	}
	public double calcuPerimeter() {
		double perimeter =  2 * (width + height);
		return perimeter;
	}
	public double calcuArea() {
		double are =width * height;
		return are;
	}
	public void getType() {
		System.out.println("我是一个矩形！");
	}
}
/**
 * 圆
 * @author dell
 *
 */
class Circle extends Shape{
	double r;
	public Circle(double r) {
		this.r = r;
	}
	public double calcuPerimeter() {
		double perimeter = 2 * Math.PI * r;
		return perimeter;
	}
	public double calcuArea() {
		double are = Math.PI * r * r;
		return are;
	}
	public void getType() {
		System.out.println("我是一个圆形！");
	}
}
/**
 * 梯形
 * @author dell
 *
 */
class Trapezoid extends Shape{
	double u;
	double d;
	double y;
	double z;
	double h;
	public Trapezoid(double u,double d,double y,double h){
	this.u=u;
	this.d=d;
	this.y=y;
	this.h=h;
	}
	public double calcuPerimeter(){
		double perimeter=u+d+y+z;
		return perimeter;	
	}
public double calcuArea(){
	double ji=1/2*(u+d)*h;
	return ji;}
	public void getType() {
		System.out.println("我是一个梯形！");
}
}
/**
 * 平行四边形
 * @author dell
 *
 */
class Pingxing extends Shape{
	double c;
	double x;
	double g;
	public Pingxing(double c,double x,double g){
		this.c=c;
		this.x=x;
		this.g=g;
	}
	public double calcuPerimeter(){
		double perimeter=(c+x)*2;
		return perimeter;
	}
	public double calcuArea(){
		double mian=c*g;
		return mian;}
		public void getType() {
			System.out.println("我是一个平行四边形！");
	}
}
public class Graphice {
	public static void main( String[] args ){
		test();
	}
	public static void test(){
		prtMenu();
		Scanner sc = new Scanner( System.in );
		int shapeType = sc.nextInt();
		switch (shapeType) {
		case 1: createTriangle();break;
		case 2:createRect();break;
		case 3:createCircle();break;
		case 4:createTrapezoid();break;
		case 5:createPingxing();break;
		default: prt();break;
		}
	}
	public static void prtMenu(){
		System.out.println();
		System.out.println( "--------请选择你要创建的图形--------" );
		System.out.println( "[1] 三角形" );
		System.out.println( "[2] 矩形" );
		System.out.println( "[3] 圆形" );
		System.out.println( "[4] 梯形" );
		System.out.println( "[5] 平行四边形" );
		System.out.println();
	}
	/**
	 * 有误
	 */
	public static void prt(){
		System.err.println("输入代号有误，请输入 1，2 ，3 ，4，5 谢谢！");
		Graphice.main(null);
	}
	/**
	 * 三角形
	 */
	public static void createTriangle(){
		Shape triangle;
		System.out.println("------------三角形---------------");
		Scanner sc2 = new Scanner( System.in );
		System.out.println("请输入三角形三边！");
		double a = sc2.nextDouble();
		double b = sc2.nextDouble();
		double c = sc2.nextDouble();
		//三角形三边合法性
		if (a > 0 && b > 0 && c > 0 && 
				(a + b) > c && (a + c) > b && (b + c) > a) {
			triangle = new Triangle(a,b,c);
			triangle.getType();
			System.out.println("三角形的面积 = " + triangle.calcuArea());
			System.out.println("三角形的面积 = " + triangle.calcuPerimeter());
		}else {
			System.out.println("\n三角形三边不合法! 三角形创建失败! "
					+ "\n请重新输入三边\n");
			createTriangle();
		}
	}
	/**
	 * 圆
	 */
	public	static void createCircle(){
		System.out.println("--------------圆----------------");
		Scanner sc1 = new Scanner( System.in );
		System.out.println("请输入圆的半径 r ");
		double r = sc1.nextDouble();
		Shape circle = new Circle(r);
		circle.getType();
		System.out.println("圆的面积 = " + circle.calcuArea());
		System.out.println("圆的周长 = " + circle.calcuPerimeter());
	}
	/**
	 * 矩形
	 */
	public	static void createRect(){
		System.out.println("--------------矩形----------------");
		Scanner sc3 = new Scanner( System.in );
		System.out.println("请输入矩形的宽和高! ");
		double width = sc3.nextDouble();
		double height = sc3.nextDouble();
		Shape rect = new Rect(width,height);
		rect.getType();
		System.out.println("矩形的面积 = " + rect.calcuArea());
		System.out.println("矩形的周长 = " + rect.calcuPerimeter());
	}
	/**
	 * 梯形
	 */
		public static void createTrapezoid(){
			System.out.println("-------------梯形-----------------");
			Scanner sc4 = new Scanner( System.in );
			System.out.println("请输入梯形的上底u,下底d,邻边y,z ");
			double u= sc4.nextDouble();
			double d= sc4.nextDouble();
			double y= sc4.nextDouble();
			double z= sc4.nextDouble();
			Shape Trapezoid = new Trapezoid(u, d, y, z);
			Trapezoid.getType();
			System.out.println("梯形的面积 = " + Trapezoid.calcuArea());
			System.out.println("梯形的周长 = " + Trapezoid.calcuPerimeter());
		}
		/**
		 * 平行四边形
		 */
		public	static void createPingxing(){
			System.out.println("--------------平行四边形----------------");
			Scanner sc1 = new Scanner( System.in );
			System.out.println("请输入平行四边形的c,x,g ");
			double c = sc1.nextDouble();
			double x = sc1.nextDouble();
			double g = sc1.nextDouble();
			Shape Pingxing = new Pingxing(c, x, g);
			Pingxing.getType();
			System.out.println("平行四边形的面积 = " + Pingxing.calcuArea());
			System.out.println("平行四边形的周长 = " + Pingxing.calcuPerimeter());
		}
	}

