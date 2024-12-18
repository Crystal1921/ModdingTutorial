# 10.2 Forge提供的Capability

当然，Forge也为你准备好了部分现有的Capability轮子

Forge提供三种Capability：`IItemHandler`、`IFluidHandler`和`IEnergyStorage`。

`IItemHandler`公开了一个用于处理物品栏Slot的接口。它可以应用于`BlockEntity`（箱子、机器等）、`Entity`（额外的玩家Slot、生物/生物物品栏/袋子）或`ItemStack`（便携式背包等）。它用一个自动化友好的系统取代了旧的`Container`和`WorldlyContainer`。

`IFluidHandler`公开了一个用于处理流体物品栏的接口。它也可以应用于`BlockEntitiy`、`Entity`或`ItemStack`。

`IEnergyStorage`公开了一个用于处理能源容器的接口。它可以应用于`BlockEntity`、`Entity`或`ItemStack`。它基于TeamCoFH的RedstoneFlux API。

以下给出一个方块实体使用`ForgeCapabilities.ITEM_HANDLER`的案例

首先，你得需要一个实现了`IItemHandler`接口的对象，这里我们可以使用`ItemStackHandler`，如果有需要，你也可以自己实现一个


``` java
    final LazyOptional<IItemHandler> itemStackHandler = LazyOptional.of(() -> new ItemStackHandler(1));
```

下面就是覆写`getCapability`方法

``` java
    @Override
    public @NotNull <T> LazyOptional<T> getCapability(@NotNull Capability<T> cap, @org.jetbrains.annotations.Nullable Direction side) {
        if (cap == ForgeCapabilities.ITEM_HANDLER) {
            return itemStackHandler.cast();
        }
        return super.getCapability(cap, side);
    }
    @Override
    public void invalidateCaps() {
        this.itemStackHandler.invalidate();
        super.invalidateCaps();
    }
```

这样，就成功使用了Forge已经提供好的Capability来实现在方块实体中持久化存储物品