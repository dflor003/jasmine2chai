jasmine2chai[![Build Status](https://travis-ci.org/fivetanley/jasmine2chai.svg?branch=master)](https://travis-ci.org/fivetanley/jasmine2chai)[![JavaScript Style Guide](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com/)
-------

## Introduction

Are you migrating your test suite from Jasmine to Mocha? Are you using
chai as your assertion library in Mocha?

While Jasmine and Mocha have a very similar test and assertion syntax,
they're just different enough to not work out of the box with each
other.

Jasmine2Chai uses
[jscodeshift](https://github.com/facebook/jscodeshift) to (as accurately
as possible) transform your test code into something that is compatible
with chai.js assertions, *while leaving your code style alone.*

## Installation

`npm install -g jasmine2chai`

## Usage

Print out a converted file to the terminal (stdout):

```
jasmine2chai myfile.js
```

## Translations

### toBe -> to.be

Jasmine assertion:

```javascript
expect('taco').toBe('taco');
```

chai assertion:

```javascript
expect('taco').to.be('taco');
```

### toEqual -> to.equal

Jasmine assertion:

```javascript
expect('taco').toEqual('taco');
```

chai assertion:

```javascript
expect('taco').to.equal('taco');
```

### toMatch -> to.match

Jasmine assertion:

```javascript
expect('taco').toMatch(/taco/)
```

chai assertion:

```javascript
expect('taco').to.match(/taco/);
```

### toBeDefined -> not.to.be.undefined

Jasmine assertion:

```javascript
expect('taco').toBeDefined();
```

chai assertion:

```javascript
expect('taco').to.not.be.undefined;
```

### toBeUndefined -> to.be.undefined

Jasmine assertion:

```javascript
expect(undefined).toBeUndefined();
```

chai assertion:

```javascript
expect(undefined).to.be.undefined;
```

### toBeNull -> to.be.null

Jasmine assertion:

```javascript
expect(null).toBeNull();
```

chai assertion:

```javascript
expect(null).to.be.null;
```

### toBeTruthy -> to.be.ok

Jasmine assertion:

```javascript
expect(true).toBeTruthy();
```

chai assertion:

```javascript
expect(true).to.be.ok;
```

### toBeFalsy -> to.not.be.ok

Jasmine assertion:

```javascript
expect(false).toBeFalsy();
```

chai assertion:

```javascript
expect(false).to.not.be.ok;
```

### toContain -> to.include

Jasmine assertion:

```javascript
expect([1, 2, 3]).toContain(1);
```

chai assertion:

```javascript
expect([1, 2, 3]).to.include(1);
```

### toBeLessThan -> to.be.below

Jasmine assertion:

```javascript
expect(1).toBeLessThan(2);
```

chai assertion:

```javascript
expect(1).to.be.below(2);
```

### toBeGreaterThan -> to.be.above;

Jasmine assertion:

```javascript
expect(2).toBeGreaterThan(1);
```

chai assertion:

```javascript
expect(2).to.be.above(1);
```

### toBeCloseTo -> to.be.closeTo

Jasmine assertion:

```javascript
expect(2).toBeCloseTo(1,1);
```

chai assertion:

```javascript
expect(2).to.be.closeTo(1,1);
```

### toThrow -> to.throw

Jasmine assertion:

```javascript
expect(function() { throw new Error('hi')).toThrow();
```

chai assertion:

```javascript
expect(function() { throw new Error('hi')).to.throw();
```

### toThrowError -> to.throw

Jasmine assertion:

```javascript
expect(foo).toThrowError("foo bar baz");
expect(foo).toThrowError(/bar/);
expect(foo).toThrowError(TypeError);
expect(foo).toThrowError(TypeError, "foo bar baz");
```

chai assertion:

```javascript
expect(foo).to.throw("foo bar baz");
expect(foo).to.throw(/bar/);
expect(foo).to.throw(TypeError);
expect(foo).to.throw(TypeError, "foo bar baz");
```

## Spy Migrations

**Important Note**:

You'll need the [sinon-chai](https://github.com/domenic/sinon-chai)
plugins for this to work. In addition, `spyOn` calls are not yet
translated. This only translates the assertions on spies.

### toHaveBeenCalled -> to.have.been.called

Jasmine assertion:

```javascript
expect(foo.setBar).toHaveBeenCalled();
```

chai assertion:

```javascript
expect(foo.setBar).to.have.been.called;
```

### toHaveBeenCalledWith -> to.have.been.calledWith

Jasmine assertion:

```javascript
expect(foo.setBar).toHaveBeenCalledWith(123);
expect(foo.setBar).toHaveBeenCalledWith(456, 'another param');
```

chai assertion:

```javascript
expect(foo.setBar).to.have.been.calledWith(123);
expect(foo.setBar).to.have.been.calledWith(456, 'another param');
```

### toHaveBeenCalledTimes -> to.have.callCount

Jasmine assertion:

```javascript
expect(foo.setBar).toHaveBeenCalledTimes(2);
```

chai assertion:

```javascript
expect(foo.setBar).to.have.callCount(2);
```

