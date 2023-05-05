---
id: "Visitor Pattern"
aliases: []
tags:
  - "CS132"
---

- Consider the following subset of MiniJava:
  $$
  \begin{aligned}
    e&\coloneqq e_1 \&\& e_2 \\
    &\mid e_1 < e_2 \\
    &\mid e_1 + e_2 \\
    &\mid e_1 - e_2 \\
    &\mid e_1 * e_2 \\
    &\mid p \\
    &\mid if\ (e)\ e\ else\ e \\
    p&\coloneqq true \\
    &\mid false \\
    &\mid\ !p \\
    &\mid \langle integer\_literal\rangle
  \end{aligned}
  $$

```java
public abstract class Expression { }
public abstract class PrimaryExpression extends Expression { }

public class IfExpression extends Expression {
  public Expression test;
  public Expression if_case;
  public Expression else_case;
}

public class IntLiteral extends PrimaryExpression {
  public int num;
}

// if (true && false) (1 + 2 + 5) else (2 * 2 * 1)
// Return type, arguments
public interface ExpressionVisitor<R, A> {
  R visit(AndExpression andExpression, A args);
}
// Every class should have an accept method
// Maybe let the accept method have a void return type, and change <R, A>
public <R, A> accept(ExpressionVisitor<R, A> visitor, A args);

public class Value { }
public class BoolValue extends Value {
  public boolean val;
}

// Value represents the type of the return
public class EvalVisitor implements ExpressionVisitor<Value, Object>{
  @override
  public Value visit(AndExpression andExpression, Object args) {
    BoolValue p1 = (BoolValue) andExpression.p1.accept(this, args);
    BoolValue p2 = (BoolValue) andExpression.p2.accept(this, args);
    // Or raise an exception if you are type-checking
    return BoolValue {
      val = p1.val && p2.val;
    };
  }
}

public class MinusExpression implements Node {
  public PrimaryExpression f0;
  public NodeToken f1;
  public PrimaryExpression f2;
}

public class Main {
  public static void main() throws ParseException {
    MiniJavaParser p = new MiniJavaParser(System.in);
    Goal m = p.goal();
    m.accept(Visitor, args*);
  }
}
```

- Must make sure that there is no overloading
