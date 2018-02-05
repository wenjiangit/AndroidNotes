### hashCode与equals

- 当覆盖一个类的`equals`方法时必须覆盖这个类`hashCode`方法,否则可能导致在HashMap,`HashSet`这些依靠`hash`算法工作的集合不能正常工作.
- 如果两个对象的`hashCode`相等,则它们的`equals`方法应该返回true.

